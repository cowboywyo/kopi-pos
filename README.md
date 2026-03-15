# Kopi Corner POS

A lightweight, zero-dependency Point of Sale system for Malaysian coffee shops (kopitiam). Built with vanilla JavaScript — no build step, no frameworks, just open `index.html` and go.

## Features

- **Menu Management** — 7 categories, 50+ items with emoji icons and price tags
- **Cart & Checkout** — Tap to add, adjust quantities, auto-calculated SST (8%)
- **Bluetooth Thermal Printing** — ESC/POS compatible 80mm receipt printers via Web Bluetooth
- **Order History** — Persistent storage with IndexedDB, daily summaries, reprint past receipts
- **Audio Feedback** — Web Audio API beeps with mute toggle
- **PWA Ready** — Add to iPad/tablet home screen for full-screen kiosk mode
- **Offline First** — Works without internet (except Google Fonts on first load)

## Quick Start

1. Open `index.html` in Chrome or Safari (iPadOS 16+)
2. Start adding items to the cart
3. Tap **Charge** to complete an order

For thermal printing, tap the printer icon in the header to connect a Bluetooth printer.

## Supported Printers

Any ESC/POS compatible 80mm Bluetooth thermal printer. Tested brands:

- Xprinter
- MUNBYN
- GOOJPRT
- PeriPage
- NETUM
- MHT

## Browser Requirements

| Feature | Browser |
|---------|---------|
| Core POS | Any modern browser |
| Bluetooth Printing | Chrome 56+, Safari 16+ (iPadOS) |
| Order History | Any browser with IndexedDB |

## Configuration

Edit the `CONFIG` object at the top of the `<script>` section in `index.html`:

```javascript
const CONFIG = {
  TAX_RATE: 0.08,           // 8% SST
  TAX_LABEL: 'SST (8%)',
  RECEIPT_WIDTH: 48,        // thermal printer character width
  SHOP_NAME: 'KOPI CORNER',
  SHOP_ADDRESS_1: 'Lot 12, Jalan Kopitiam',
  SHOP_ADDRESS_2: '10200 George Town, Penang',
  SHOP_PHONE: 'Tel: 04-123 4567',
  CURRENCY: 'RM',
  // ... more options
};
```

## Menu Customization

Edit the `MENU` object to add/remove/modify items:

```javascript
const MENU = {
  "Category Name": [
    { name: "Item Name", emoji: "icon", price: 3.00, tag: "Label" },
  ],
};
```

## Architecture

Single-file SPA — all HTML, CSS, and JavaScript in `index.html`. Key components:

- **ThermalPrinter** class — Web Bluetooth ESC/POS driver
- **OrderDB** class — IndexedDB wrapper for order persistence
- **CONFIG** — Centralized configuration constants
- **Rendering functions** — DOM-based UI with manual state management

## License

MIT
