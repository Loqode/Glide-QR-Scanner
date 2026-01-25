# Glide-QR-Scanner

A minimal web app that scans QR codes and POSTs the result to a webhook you specify using a URL query parameter.

It uses the [`html5-qrcode`](https://github.com/mebjas/html5-qrcode) library via CDN.

---

## Features

- 📷 Uses the device camera (rear camera preferred) to scan QR codes  
- ✅ Shows a full-screen overlay with the scanned data  
- 🟦 **Confirm** sends the scanned text to your webhook via `fetch()` (POST, `text/plain`)  
- ❌ **Cancel** closes the overlay and resumes scanning  
- ⏸️ Pauses scanning while the overlay is visible (camera stays on)

---

## How it works

1. The scanner starts automatically when the page loads.
2. When a QR code is detected:
   - The decoded text is shown in a confirmation overlay.
   - Scanning is paused to prevent duplicate reads.
3. User action:
   - **Confirm** → sends the scanned text to the webhook endpoint and resumes scanning.
   - **Cancel** → dismisses the overlay and resumes scanning.

---

## Usage

### 1) Open the app URL

Host or open the HTML file in a browser (HTTPS or `localhost` required for camera access).

### 2) Specify your webhook endpoint

Pass your webhook URL using the `endpoint` query parameter:

https://your-site.com/index.html?endpoint=https://example.com/webhook

When **Confirm** is pressed, the scanned QR text is sent as the request body to that URL.
