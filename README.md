import 'dart:typed_data';
import 'package:flutter/material.dart';
import 'package:qr_code_scanner/qr_code_scanner.dart';
import 'package:qr_flutter/qr_flutter.dart';
import 'package:image/image.dart' as img;
import 'package:flutter/services.dart';
import 'package:path_provider/path_provider.dart';
import 'dart:io';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'QR to QRIS Converter',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const HomePage(),
    );
  }
}

// ==================== HALAMAN UTAMA ====================
class HomePage extends StatelessWidget {
  const HomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('QR to QRIS Converter'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            const Text(
              'Konversi QR Code apapun\nmenjadi QR dengan tampilan QRIS',
              textAlign: TextAlign.center,
              style: TextStyle(fontSize: 18),
            ),
            const SizedBox(height: 30),
            ElevatedButton.icon(
              icon: const Icon(Icons.qr_code_scanner),
              label: const Text('Scan QR Code'),
              onPressed: () {
                Navigator.push(
                  context,
                  MaterialPageRoute(builder: (context) => const ScanPage()),
                );
              },
            ),
          ],
        ),
      ),
    );
  }
}

// ==================== HALAMAN SCAN ====================
class ScanPage extends StatefulWidget {
  const ScanPage({super.key});

  @override
  State<ScanPage> createState() => _ScanPageState();
}

class _ScanPageState extends State<ScanPage> {
  final GlobalKey qrKey = GlobalKey(debugLabel: 'QR');
  QRViewController? controller;
  String? qrText;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Scan QR Code'),
      ),
      body: Column(
        children: <Widget>[
          Expanded(
            flex: 5,
            child: QRView(
              key: qrKey,
              onQRViewCreated: _onQRViewCreated,
            ),
          ),
          Expanded(
            flex: 1,
            child: Center(
              child: (qrText != null)
                  ? Text('Hasil: $qrText')
                  : const Text('Arahkan kamera ke QR code'),
            ),
          )
        ],
      ),
    );
  }

  void _onQRViewCreated(QRViewController controller) {
    this.controller = controller;
    controller.scannedDataStream.listen((scanData) {
      setState(() {
        qrText = scanData.code;
      });
      if (qrText != null) {
        Navigator.pushReplacement(
          context,
          MaterialPageRoute(
            builder: (context) => ResultPage(qrData: qrText!),
          ),
        );
      }
    });
  }

  @override
  void dispose() {
    controller?.dispose();
    super.dispose();
  }
}

// ==================== HALAMAN HASIL ====================
class ResultPage extends StatelessWidget {
  final String qrData;

  const ResultPage({super.key, required this.qrData});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Hasil Konversi'),
        actions: [
          IconButton(
            icon: const Icon(Icons.save),
            onPressed: () => _saveQrCode(context),
          ),
        ],
      ),
      body: SingleChildScrollView(
        child: Center(
          child: Padding(
            padding: const EdgeInsets.all(20.0),
            child: Column(
              children: [
                const Text(
                  'QR Code dengan Tampilan QRIS',
                  style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold),
                ),
                const SizedBox(height: 20),
                FutureBuilder<Uint8List>(
                  future: _generateQrWithLogo(),
                  builder: (context, snapshot) {
                    if (snapshot.connectionState == ConnectionState.done) {
                      return Image.memory(snapshot.data!);
                    } else {
                      return const CircularProgressIndicator();
                    }
                  },
                ),
                const SizedBox(height: 20),
                const Text(
                  'Data QR Code:',
                  style: TextStyle(fontWeight: FontWeight.bold),
                ),
                Container(
                  padding: const EdgeInsets.all(10),
                  decoration: BoxDecoration(
                    border: Border.all(color: Colors.grey),
                    borderRadius: BorderRadius.circular(5),
                  ),
                  child: Text(
                    qrData,
                    textAlign: TextAlign.center,
                    style: const TextStyle(fontSize: 12),
                  ),
                ),
                const SizedBox(height: 20),
                const Text(
                  'Ketika dipindai, QR ini akan mengarah ke data asli',
                  style: TextStyle(fontStyle: FontStyle.italic),
                ),
              ],
            ),
          ),
        ),
      ),
    );
  }

  Future<Uint8List> _generateQrWithLogo() async {
    // Generate QR code image
    final qrImage = await QrPainter(
      data: qrData,
      version: QrVersions.auto,
      gapless: false,
    ).toImageData(300);

    // Load QRIS logo
    final ByteData logoData = await rootBundle.load('assets/qris_logo.png');
    final Uint8List logoBytes = logoData.buffer.asUint8List();
    img.Image? logoImage = img.decodeImage(logoBytes);

    // Decode QR code
    img.Image? qrCodeImage = img.decodeImage(qrImage!.buffer.asUint8List());

    if (qrCodeImage != null && logoImage != null) {
      // Resize logo (20% dari ukuran QR)
      final logoSize = (qrCodeImage.width * 0.2).round();
      logoImage = img.copyResize(logoImage, width: logoSize, height: logoSize);

      // Posisi logo di tengah
      final offsetX = (qrCodeImage.width - logoImage.width) ~/ 2;
      final offsetY = (qrCodeImage.height - logoImage.height) ~/ 2;

      // Gabungkan logo dengan QR
      img.Image finalImage = img.Image(qrCodeImage.width, qrCodeImage.height);
      img.compositeImage(finalImage, qrCodeImage);
      img.compositeImage(finalImage, logoImage, dstX: offsetX, dstY: offsetY);

      return Uint8List.fromList(img.encodePng(finalImage));
    } else {
      throw Exception('Gagal generate QR code');
    }
  }

  void _saveQrCode(BuildContext context) async {
    try {
      final imageBytes = await _generateQrWithLogo();
      final directory = await getApplicationDocumentsDirectory();
      final path = '${directory.path}/qris_qr.png';
      final file = File(path);
      await file.writeAsBytes(imageBytes);

      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(
          content: Text('QR Code disimpan di: $path'),
          action: SnackBarAction(
            label: 'OK',
            onPressed: () {},
          ),
        ),
      );
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('Gagal menyimpan: ${e.toString()}')),
      );
    }
  }
}
