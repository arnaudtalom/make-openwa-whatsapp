# OpenWA WhatsApp Integration for Make.com 🚀

[![Make.com Verified App](https://img.shields.io/badge/Make.com-Custom%20App-purple?style=flat-square&logo=make)](https://www.make.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=flat-square)](LICENSE)
[![WhatsApp API](https://img.shields.io/badge/WhatsApp-OpenWA-25D366?style=flat-square&logo=whatsapp)](https://openwa.dev)

Automate WhatsApp messaging, send rich media (photos with previews, PDF documents, audio, videos), verify phone numbers, and manage communication workflows on **Make.com** using your **OpenWA** server.

---

## 📑 Table of Contents
- [Prerequisites](#-prerequisites)
- [How to Connect OpenWA to Make](#-how-to-connect-openwa-to-make)
- [Available Modules](#-available-modules)
  - [1. Send a Text Message](#1-send-a-text-message)
  - [2. Send a File / Media](#2-send-a-file--media)
  - [3. Check WhatsApp Number](#3-check-if-number-exists-on-whatsapp)
  - [4. Get Session Status](#4-get-session-status)
  - [5. Make an API Call](#5-make-an-api-call)
- [Phone Number Format Guidelines](#-phone-number-formatting)
- [Troubleshooting & FAQ](#-troubleshooting--faq)
- [Legal & Privacy](#-legal--privacy)

---

## 🔌 Prerequisites

Before setting up your scenarios in Make, ensure you have:
1. A running **OpenWA server** instance (hosted on a VPS, Docker container, or cloud server).
2. Your **OpenWA Server URL** (e.g. `http://your-vps-ip:2785` or `https://whatsapp.yourdomain.com`).
3. Your secret **API Key** (`X-API-Key`).
4. An active, connected **WhatsApp Session ID** (scanned via QR code on your mobile WhatsApp).

---

## 🔑 How to Connect OpenWA to Make

1. In your Make scenario, add any **OpenWA WhatsApp** module.
2. In the module configuration, click **Create a connection**.
3. Fill in your credentials:
   - **OpenWA Server URL**: Your full server URL with port (e.g. `http://217.76.52.74:2785`).
   - **API Key**: Your secret API token (passed via `X-API-Key`).
   - **Session ID**: The active WhatsApp session identifier / UUID.
4. Click **Save**. Make will verify the connection with your server.

---

## 📦 Available Modules

### 1. Send a Text Message
Sends instant text messages to WhatsApp phone numbers or groups.
- **Phone Number / Chat ID**: The recipient's number in international format (e.g., `14155552671` or `237699000000`).
- **Message Text**: The message content. Supports line breaks, emojis, and WhatsApp text formatting (`*bold*`, `_italic_`, `~strikethrough~`).

### 2. Send a File / Media
Sends images with full in-chat visual previews, PDF documents, audio tracks, or videos via a public URL.
- **Media Type**: Choose between:
  - `Image (with Visual Photo Preview)`: Displays directly as a photo in chat with caption.
  - `Document / PDF / Attachment`: Displays as a downloadable file card.
  - `Audio File`: Sends an audio clip.
  - `Video File`: Sends a video message.
- **File URL**: A publicly accessible direct link to the media file.
- **Caption**: Optional caption text displayed directly beneath the photo or document.
- **File Name**: Required only when sending Document types (e.g. `invoice_1042.pdf`).

### 3. Check if Number Exists on WhatsApp
Verifies if a specific phone number has an active WhatsApp account before sending messages.
- **Phone Number**: The number to test in international format.
- **Output**: Returns `exists: true/false` and the verified `chatId`.

### 4. Get Session Status
Fetches the real-time operational status, device battery level, and user profile information of your connected WhatsApp session.

### 5. Make an API Call
Execute any arbitrary authorized HTTP endpoint against your OpenWA REST API.

---

## 📱 Phone Number Formatting

You can pass phone numbers in any of the following standard formats — the module automatically cleans spaces, plus signs, and dashes:
- `+1 (415) 555-2671` ➔ formatted to `14155552671@c.us`
- `237699112233` ➔ formatted to `237699112233@c.us`
- `120363025112345678@g.us` (Group Chat ID)

---

## ❓ Troubleshooting & FAQ

#### Q: The image was sent as an attachment without preview. Why?
**A:** Make sure you selected `Image (with Visual Photo Preview)` under **Media Type** instead of `Document`. Images sent to `/send-image` display natively in chat with full preview.

#### Q: Error `[400] WhatsApp could not resolve the recipient`
**A:** This means the recipient phone number is either not on WhatsApp, or the session needs an initial interaction. Use the **Check WhatsApp Number** module to verify contacts beforehand.

---

## 📜 Legal & Privacy

- [Privacy Policy](PRIVACY.md)
- [Terms of Service](TERMS.md)

---

## 📄 License
This integration is distributed under the [MIT License](LICENSE).
