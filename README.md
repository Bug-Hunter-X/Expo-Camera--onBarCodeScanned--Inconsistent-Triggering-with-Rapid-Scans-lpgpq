# Expo Camera Barcode Scanning Bug

This repository demonstrates a bug in Expo's Camera API where the `onBarCodeScanned` function doesn't always trigger reliably when scanning multiple barcodes quickly.  The bug causes missed barcode readings, impacting applications relying on accurate and timely barcode data acquisition.

## Bug Description

The `onBarCodeScanned` callback function within Expo's Camera API shows inconsistent behavior. When scanning barcodes in rapid succession, some scans are missed; the callback function doesn't fire for every successfully scanned barcode. This results in incomplete or inaccurate data.

## Reproduction Steps

1. Clone the repository.
2. Install dependencies: `npm install`
3. Run the app: `expo start`
4. Point the camera at barcodes and scan them rapidly. Note that not all barcodes are detected.

## Solution

The provided solution modifies how the barcode scan event is handled to ensure every scan is processed. This involves debouncing the event handling to prevent rapid successive calls from being dropped. See `bugSolution.js` for details.