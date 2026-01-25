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

## Usage (Glide)

### 1) Copy the QR Scanner app URL

https://loqode.github.io/Glide-QR-Scanner

This is the base URL you will embed inside Glide.

---

### 2) Create a Glide workflow with a Webhook trigger

In Glide:
- Create a new workflow
- Add a **Webhook** trigger
- Copy the generated **Webhook URL**

This webhook will receive the scanned QR text.

---

### 3) Append the Glide webhook to the scanner URL

In Glide, use a **Construct URL**, **Template**, or dynamic value to append the webhook URL as the `endpoint` query parameter.

Example:

https://loqode.github.io/Glide-QR-Scanner?endpoint=https://go.glideapps.com/api/container/plugin/webhook-trigger/ABC/12345

---

### 4) Use the constructed URL in a Web Embed component

Paste the constructed URL into a **Web Embed** component in the Glide Layout Editor.

---

### What happens on scan

- The camera scans a QR code
- The scanned value is shown for confirmation
- When **Confirm** is pressed, the QR text is sent as the **request body** to the Glide webhook
- The scanner then resumes automatically
