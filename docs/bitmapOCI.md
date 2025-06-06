# bitmapOCI.js - Bitcoin Bitmap On-Chain Index

## Overview
Bitcoin bitmap on-chain index (OCI) module for accessing bitmap inscription data from ordinal inscriptions 0 to 839,999, with support for reinscriptions and delta compression.

## Author
Thanks to @_lefrog for finding and fixing multiple bugs - reinscriptions are now properly accounted for.

## Purpose
- Provides access to complete bitmap inscription index
- Handles delta-compressed data for efficiency
- Manages reinscription tracking
- Enables bitmap discovery and verification

## Key Features

### Data Range
- **Coverage**: Bitmap ordinals 0 to 839,999
- **Pages**: 8 total pages of data
- **Format**: Delta-compressed satoshi numbers
- **Reinscriptions**: Properly handled and tracked

### Page Structure
```javascript
const allPages = [
    '/content/01bba6c58af39d7f199aa2bceeaaba1ba91b23d2663bc4ef079a4b5e442dbf74i0',
    '/content/bb01dfa977a5cd0ee6e900f1d1f896b5ec4b1e3c7b18f09c952f25af6591809fi0',
    '/content/bb02e94f3062facf6aa2e47eeed348d017fd31c97614170dddb58fc59da304efi0',
    '/content/bb037ec98e6700e8415f95d1f5ca1fe1ba23a3f0c5cb7284d877e9ac418d0d32i0',
    '/content/bb9438f4345f223c6f4f92adf6db12a82c45d1724019ecd7b6af4fcc3f5786cei0',
    '/content/bb0542d4606a9e7eb4f31051e91f7696040db06ca1383dff98505618c34d7df7i0',
    '/content/bb06a4dffba42b6b513ddee452b40a67688562be4a1345127e4d57269e6b2ab6i0',
    '/content/bb076934c1c22007b315dd1dc0f8c4a2f9d52f348320cfbadc7c0bd99eaa5e18i0',
    '/content/bb986a1208380ec7db8df55a01c88c73a581069a51b5a2eb2734b41ba10b65c2i0'
];
```

## Core Functions

### `fillPage(page)`
Loads and processes data for a specific page index.
- Fetches data from recursive endpoints
- Handles inconsistent formatting (pages 2 & 3)
- Reconstructs full satoshi numbers from deltas
- Processes both satoshi and inscription ID arrays

### `getBitmapSatsRange(start, end)`
Retrieves bitmap satoshi numbers within a specified range.
```javascript
// Get full list of all bitmaps
const allBitmaps = await getBitmapSatsRange(0, 839999);

// Get specific range
const subset = await getBitmapSatsRange(1000, 2000);
```

### Data Processing
```javascript
// Rebuild full sat numbers from deltas
const fullSats = []
data[0].forEach((sat, i) => {
    if (i === 0) {
        fullSats.push(parseInt(sat))
    } else {
        fullSats.push(parseInt(fullSats[i-1]) + parseInt(sat))
    }
});
```

## Usage Examples

### Get Complete Bitmap Index
```javascript
import { getBitmapSatsRange } from 'bitmapOCI';

// Get all bitmap inscriptions
const allBitmaps = await getBitmapSatsRange(0, 839999);
console.log(`Total bitmaps: ${allBitmaps.length}`);
```

### Range Queries
```javascript
// Get bitmaps in specific range
const earlyBitmaps = await getBitmapSatsRange(0, 999);
const midBitmaps = await getBitmapSatsRange(100000, 200000);
const lateBitmaps = await getBitmapSatsRange(800000, 839999);
```

### Custom Origin Server
```javascript
// Use custom ordinal server
const bitmaps = await getBitmapSatsRange(0, 1000, 'https://ordinals.com');
```

### Bitmap Verification
```javascript
async function isBitmap(satNumber) {
    const allBitmaps = await getBitmapSatsRange(0, 839999);
    return allBitmaps.includes(satNumber);
}

// Check if specific sat is a bitmap
const isValid = await isBitmap(257418248345168);
```

## Data Format

### Input Format
- **Delta Arrays**: Compressed differences between consecutive satoshi numbers
- **JSON Format**: Structured data with formatting variations
- **Reinscription Handling**: Latest inscriptions override previous ones

### Output Format
- **Full Satoshi Numbers**: Reconstructed from deltas
- **Inscription IDs**: Corresponding ordinal inscription identifiers
- **Sorted Arrays**: Ordered by satoshi number

## Error Handling
- Handles inconsistent JSON formatting
- Manages network failures gracefully
- Processes malformed data entries
- Validates page boundaries

## Performance Optimizations
- **Page Caching**: Loads pages only when needed
- **Delta Compression**: Reduces data size
- **Range Queries**: Efficient subset loading
- **Memory Management**: Prevents memory leaks

## Origin Parameter Support
Uses `?origin=` query parameter to set URL beginnings:
```javascript
// Example: https://ordinals.com/content/...
const url = new URL(import.meta.url);
const params = new URLSearchParams(url.search);
let originParam = params.get('origin');
```

## Integration
- Works with recursive endpoints
- Compatible with ordinal servers
- Supports bitmap verification
- Enables bitmap discovery tools

## Related Files
- `recursive-endpoints.js` - Core recursive endpoint utilities
- `bitmon.js` - Bitcoin monitoring functionality
- Page data inscriptions (referenced in allPages array)

## Use Cases
- Bitmap verification systems
- Ordinal marketplace integration
- Collection analysis tools
- Bitmap discovery applications
- Investment tracking platforms
