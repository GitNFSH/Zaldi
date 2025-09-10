/* ==UserStyle==
@name         GitHub Cyber Security Theme
@namespace    github.com/cyber-theme
@version      1.0
@description  Transform GitHub into a Cyber Security themed interface
@author       CyberDev
==/UserStyle== */

@-moz-document domain("github.com") {
    :root {
        --cyber-green: #00ff41;
        --cyber-blue: #00d4ff;
        --cyber-purple: #ff00ff;
        --cyber-red: #ff0040;
        --cyber-yellow: #ffff00;
        --cyber-dark: #0a0a0a;
        --cyber-darker: #050505;
        --cyber-gray: #1a1a1a;
        --cyber-border: #00ff4120;
    }

    /* Background & Base Styles */
    body {
        background: var(--cyber-darker) !important;
        background-image: 
            radial-gradient(circle at 20% 50%, rgba(0, 255, 65, 0.1) 0%, transparent 50%),
            radial-gradient(circle at 80% 80%, rgba(0, 212, 255, 0.1) 0%, transparent 50%),
            radial-gradient(circle at 40% 20%, rgba(255, 0, 255, 0.1) 0%, transparent 50%);
        color: var(--cyber-green) !important;
        font-family: 'Courier New', monospace !important;
    }

    /* Matrix Rain Effect */
    body::before {
        content: "";
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(0deg, transparent 24%, rgba(0, 255, 65, 0.05) 25%, rgba(0, 255, 65, 0.05) 26%, transparent 27%, transparent 74%, rgba(0, 255, 65, 0.05) 75%, rgba(0, 255, 65, 0.05) 76%, transparent 77%, transparent);
        background-size: 50px 50px;
        pointer-events: none;
        z-index: 1;
        opacity: 0.3;
    }

    /* Header */
    .Header-old {
        background: rgba(10, 10, 10, 0.95) !important;
        border-bottom: 2px solid var(--cyber-green) !important;
        box-shadow: 0 0 20px rgba(0, 255, 65, 0.5) !important;
        backdrop-filter: blur(10px);
    }

    .Header-link {
        color: var(--cyber-green) !important;
        text-shadow: 0 0 10px var(--cyber-green) !important;
        transition: all 0.3s ease !important;
    }

    .Header-link:hover {
        color: var(--cyber-blue) !important;
        text-shadow: 0 0 20px var(--cyber-blue) !important;
        transform: translateY(-2px) !important;
    }

    /* Navigation */
    .UnderlineNav-item {
        color: var(--cyber-green) !important;
        border-bottom: 2px solid transparent !important;
        transition: all 0.3s ease !important;
    }

    .UnderlineNav-item:hover {
        color: var(--cyber-blue) !important;
        border-bottom-color: var(--cyber-blue) !important;
        text-shadow: 0 0 10px var(--cyber-blue) !important;
    }

    .UnderlineNav-item.selected {
        color: var(--cyber-purple) !important;
        border-bottom-color: var(--cyber-purple) !important;
        text-shadow: 0 0 15px var(--cyber-purple) !important;
    }

    /* Repository Cards */
    .Box {
        background: rgba(26, 26, 26, 0.8) !important;
        border: 1px solid var(--cyber-border) !important;
        border-radius: 0 !important;
        box-shadow: 
            0 0 20px rgba(0, 255, 65, 0.2),
            inset 0 0 20px rgba(0, 255, 65, 0.05) !important;
        backdrop-filter: blur(5px);
        transition: all 0.3s ease !important;
    }

    .Box:hover {
        border-color: var(--cyber-green) !important;
        box-shadow: 
            0 0 30px rgba(0, 255, 65, 0.4),
            inset 0 0 30px rgba(0, 255, 65, 0.1) !important;
        transform: translateY(-2px) !important;
    }

    /* Repository Names */
    .repo-list-item h3 a {
        color: var(--cyber-blue) !important;
        text-shadow: 0 0 10px var(--cyber-blue) !important;
        transition: all 0.3s ease !important;
    }

    .repo-list-item h3 a:hover {
        color: var(--cyber-purple) !important;
        text-shadow: 0 0 20px var(--cyber-purple) !important;
        animation: glitch 0.3s ease-in-out !important;
    }

    /* Glitch Effect */
    @keyframes glitch {
        0%, 100% { transform: translate(0); }
        20% { transform: translate(-2px, 2px); }
        40% { transform: translate(-2px, -2px); }
        60% { transform: translate(2px, 2px); }
        80% { transform: translate(2px, -2px); }
    }

    /* Buttons */
    .btn {
        background: linear-gradient(45deg, var(--cyber-gray), var(--cyber-dark)) !important;
        border: 1px solid var(--cyber-green) !important;
        color: var(--cyber-green) !important;
        text-shadow: 0 0 5px var(--cyber-green) !important;
        box-shadow: 0 0 10px rgba(0, 255, 65, 0.3) !important;
        transition: all 0.3s ease !important;
        font-family: 'Courier New', monospace !important;
    }

    .btn:hover {
        background: linear-gradient(45deg, var(--cyber-dark), var(--cyber-gray)) !important;
        border-color: var(--cyber-blue) !important;
        color: var(--cyber-blue) !important;
        text-shadow: 0 0 10px var(--cyber-blue) !important;
        box-shadow: 0 0 20px rgba(0, 212, 255, 0.5) !important;
        transform: translateY(-2px) !important;
    }

    .btn-primary {
        background: linear-gradient(45deg, var(--cyber-green), var(--cyber-blue)) !important;
        border-color: var(--cyber-green) !important;
    }

    .btn-primary:hover {
        background: linear-gradient(45deg, var(--cyber-blue), var(--cyber-purple)) !important;
        border-color: var(--cyber-blue) !important;
    }

    /* Code Blocks */
    .highlight {
        background: rgba(0, 0, 0, 0.8) !important;
        border: 1px solid var(--cyber-green) !important;
        border-radius: 0 !important;
        box-shadow: 
            0 0 20px rgba(0, 255, 65, 0.3),
            inset 0 0 20px rgba(0, 255, 65, 0.1) !important;
    }

    .highlight pre {
        background: transparent !important;
        color: var(--cyber-green) !important;
    }

    /* Terminal Style */
    .blob-code, .blob-code-inner {
        color: var(--cyber-green) !important;
        font-family: 'Courier New', monospace !important;
    }

    .blob-num {
        color: var(--cyber-blue) !important;
        background: rgba(0, 212, 255, 0.1) !important;
    }

    /* Search Bar */
    .search-input {
        background: rgba(0, 0, 0, 0.8) !important;
        border: 1px solid var(--cyber-green) !important;
        color: var(--cyber-green) !important;
        border-radius: 0 !important;
        box-shadow: inset 0 0 10px rgba(0, 255, 65, 0.2) !important;
    }

    .search-input:focus {
        border-color: var(--cyber-blue) !important;
        box-shadow: 
            inset 0 0 15px rgba(0, 212, 255, 0.3),
            0 0 20px rgba(0, 212, 255, 0.5) !important;
        outline: none !important;
    }

    /* Profile */
    .avatar-user {
        border: 2px solid var(--cyber-green) !important;
        box-shadow: 0 0 20px rgba(0, 255, 65, 0.5) !important;
        transition: all 0.3s ease !important;
    }

    .avatar-user:hover {
        border-color: var(--cyber-purple) !important;
        box-shadow: 0 0 30px rgba(255, 0, 255, 0.7) !important;
        transform: rotate(5deg) scale(1.1) !important;
    }

    /* Stats */
    .Counter {
        background: rgba(0, 255, 65, 0.1) !important;
        border: 1px solid var(--cyber-green) !important;
        color: var(--cyber-green) !important;
        text-shadow: 0 0 5px var(--cyber-green) !important;
    }

    /* Loading Animation */
    .ajax-pagination-loader {
        border: 2px solid var(--cyber-green) !important;
        border-top-color: transparent !important;
        animation: cyber-spin 1s linear infinite !important;
    }

    @keyframes cyber-spin {
        to { transform: rotate(360deg); }
    }

    /* Scrollbar */
    ::-webkit-scrollbar {
        width: 10px !important;
    }

    ::-webkit-scrollbar-track {
        background: var(--cyber-darker) !important;
        border: 1px solid var(--cyber-border) !important;
    }

    ::-webkit-scrollbar-thumb {
        background: linear-gradient(180deg, var(--cyber-green), var(--cyber-blue)) !important;
        border: 1px solid var(--cyber-green) !important;
        box-shadow: 0 0 10px rgba(0, 255, 65, 0.5) !important;
    }

    ::-webkit-scrollbar-thumb:hover {
        background: linear-gradient(180deg, var(--cyber-blue), var(--cyber-purple)) !important;
    }

    /* Terminal Command Style */
    .user-mention, .team-mention {
        background: rgba(0, 255, 65, 0.1) !important;
        border: 1px solid var(--cyber-green) !important;
        color: var(--cyber-green) !important;
        padding: 2px 6px !important;
        border-radius: 3px !important;
        font-family: 'Courier New', monospace !important;
    }

    /* Issues & Pull Requests */
    .IssueLabel {
        border: 1px solid !important;
        font-family: 'Courier New', monospace !important;
        text-transform: uppercase !important;
        letter-spacing: 1px !important;
    }

    /* Cyber Grid Background */
    .application-main {
        position: relative !important;
    }

    .application-main::after {
        content: "";
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: 
            linear-gradient(rgba(0, 255, 65, 0.1) 1px, transparent 1px),
            linear-gradient(90deg, rgba(0, 255, 65, 0.1) 1px, transparent 1px);
        background-size: 50px 50px;
        pointer-events: none;
        z-index: 0;
        opacity: 0.1;
    }

    /* Text Effects */
    h1, h2, h3, h4, h5, h6 {
        color: var(--cyber-blue) !important;
        text-shadow: 0 0 10px var(--cyber-blue) !important;
        font-family: 'Courier New', monospace !important;
        letter-spacing: 1px !important;
    }

    p, span, div {
        color: var(--cyber-green) !important;
    }

    /* Links */
    a {
        color: var(--cyber-blue) !important;
        text-decoration: none !important;
        transition: all 0.3s ease !important;
        position: relative !important;
    }

    a::before {
        content: "";
        position: absolute;
        width: 0;
        height: 1px;
        bottom: 0;
        left: 0;
        background: var(--cyber-blue) !important;
        transition: width 0.3s ease !important;
    }

    a:hover {
        color: var(--cyber-purple) !important;
        text-shadow: 0 0 10px var(--cyber-purple) !important;
    }

    a:hover::before {
        width: 100% !important;
    }

    /* Input Fields */
    input, textarea, select {
        background: rgba(0, 0, 0, 0.8) !important;
        border: 1px solid var(--cyber-green) !important;
        color: var(--cyber-green) !important;
        border-radius: 0 !important;
        font-family: 'Courier New', monospace !important;
        transition: all 0.3s ease !important;
    }

    input:focus, textarea:focus, select:focus {
        border-color: var(--cyber-blue) !important;
        box-shadow: 0 0 15px rgba(0, 212, 255, 0.5) !important;
        outline: none !important;
    }

    /* Notification Badge */
    .notification-indicator .mail-status {
        background: var(--cyber-red) !important;
        box-shadow: 0 0 20px rgba(255, 0, 64, 0.8) !important;
        animation: pulse 2s infinite !important;
    }

    @keyframes pulse {
        0% { transform: scale(1); }
        50% { transform: scale(1.2); }
        100% { transform: scale(1); }
    }
}
