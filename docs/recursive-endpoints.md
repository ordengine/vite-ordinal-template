# recursive-endpoints.js - Ordinal Data Access Library

## Overview
A comprehensive JavaScript library for accessing Bitcoin ordinal inscription data through recursive endpoints. Provides functions to query inscriptions, metadata, block information, and related data from ordinal servers.

## Author
**Eloc** - Version 2.0

## Purpose
- Access inscription and metadata information
- Query blockchain data (blocks, heights, timestamps)
- Retrieve children and parent relationships
- Fetch SAT-based inscription data
- Decode CBOR metadata

## Purpose
- Provides utilities for getting data from recursive endpoints
- Handles inscription ID extraction from URLs
- Fetches inscription information and metadata
- Enables ordinal-based application functionality

## Key Functions

### `getId()`
Extracts the inscription ID from the current page's URL.

```javascript
/**
 * @description Retrieves the inscription ID from the current page's URL.
 * Assumes the URL follows a structure like `/content/<id>` or `/preview/<id>`.
 * @returns {string} The extracted ID.
 */
export const getId = () => {
  let id = window.location.pathname.split('/')[2];
  return id;
};
```

### `getInscription(inscriptionId, origin)`
Fetches detailed information about an inscription.

```javascript
/**
 * @description Fetches information about an inscription.
 * @param {string} inscriptionId - Inscription to get info about (defaults to current page ID)
 * @param {string} origin - The origin for the fetch
 * @returns Promise<{
 *   charms: Array<string>;
 *   content_type: string;
 *   content_length: number;
 *   fee: number;
 *   height: number;
 *   number: number;
 *   output: string;
 *   sat: null | string;
 *   satpoint: string;
 *   timestamp: number;
 *   value: number;
 * } | null>
 */
export const getInscription = async (inscriptionId = getId(), origin = '') => {
  // Implementation details...
};
```

## Return Data Structure
The `getInscription` function returns an object with:
- `charms`: Array of charm identifiers
- `content_type`: MIME type of the inscription
- `content_length`: Size of the inscription in bytes
- `fee`: Bitcoin fee paid for the inscription
- `height`: Bitcoin block height
- `number`: Ordinal inscription number
- `output`: Bitcoin transaction output
- `sat`: Satoshi information (if available)
- `satpoint`: Specific satoshi location
- `timestamp`: Unix timestamp of inscription
- `value`: Bitcoin value in satoshis

## Usage Examples

### Get Current Inscription ID
```javascript
import { getId } from 'recursive-endpoints';
const currentId = getId();
```

### Fetch Inscription Data
```javascript
import { getInscription } from 'recursive-endpoints';
const inscription = await getInscription();
console.log(inscription.content_type);
```

### Fetch Specific Inscription
```javascript
import { getInscription } from 'recursive-endpoints';
const specificInscription = await getInscription('abc123...i0');
```

## Error Handling
The library includes proper error handling for:
- Network failures
- Invalid inscription IDs
- Missing or malformed data
- CORS issues

## Dependencies
- Uses browser `fetch` API
- Requires access to `window.location`
- Compatible with ordinal server endpoints

## Integration
- Essential for ordinal-based applications
- Works with Bitcoin ordinal servers
- Enables recursive content loading
- Supports dynamic inscription discovery

## Related Files
- `bitmapOCI.js` - Uses recursive endpoints for bitmap data
- `bitmon.js` - Bitcoin monitoring functionality
- All ordinal-specific scripts depend on this library
