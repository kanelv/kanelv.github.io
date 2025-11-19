---
title: "Quick OTP"
date: 2025-01-01T00:00:00+07:00
weight: 3
draft: false
tags: ["Chrome Extension", "TOTP", "2FA", "React", "TypeScript"]
---

## Overview

Quick OTP is a lightweight Chrome extension for managing and generating Time-based One-Time Passwords (TOTP) directly in the browser. It replaces or
supplements mobile authenticator apps like Google Authenticator or Authy, providing quick access to 2FA codes without reaching for your phone.

## Tech Stack

- **React 19** - UI framework with hooks for state management
- **TypeScript** - Type-safe development
- **Vite** with **@crxjs/vite-plugin** - Fast builds and Chrome extension support
- **otpauth** - TOTP generation (RFC 6238 compliant)
- **jsQR** - QR code scanning
- **React Bootstrap** - UI components
- **Chrome Storage API** - Local data persistence

## Key Features

- **OTP Management** - Add, edit, delete, and search TOTP entries
- **Multiple QR Scanning Methods** - File upload, screen capture, and clipboard paste
- **Real-time Countdown** - Visual progress bar with color-coded time indicators
- **One-click Copy** - Copy codes to clipboard with visual feedback
- **Import/Export** - Backup and restore OTP items as JSON
- **Dark Mode Support** - Automatic theme detection

## Challenges & Solutions

**QR Code Parsing**: Implemented multiple scanning methods (file, screen capture, clipboard) using jsQR library and parsing `otpauth://` URIs to
extract provider, account, and secret.

**Time Synchronization**: Used standard 30-second TOTP windows with real-time countdown updates every second, regenerating codes at window boundaries.

**State Management**: Created a custom `useOTPManager` hook to handle loading/saving from Chrome storage, timer effects, and CRUD operations while
only persisting essential data (excluding generated OTP values).

**Security Considerations**: Prepared encryption utilities (PBKDF2 + AES-GCM) for future implementation of encrypted secret storage.

## Links

- [GitHub Repository](https://github.com/kanelv/quick-otp)

## Timeline

**Started:** January 2025
**Status:** Active Development