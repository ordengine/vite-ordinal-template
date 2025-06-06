# bitmon.js - Bitcoin Network Monitor

## Overview
Real-time Bitcoin network monitoring dashboard that fetches and displays current Bitcoin price, block height, network statistics, and provides a clean interface for tracking Bitcoin blockchain data.

## Core Features
- **Real-time Bitcoin Price**: Live BTC/USD pricing from CoinGecko API
- **Block Height Tracking**: Current blockchain height and timestamp
- **Network Statistics**: Comprehensive blockchain metrics
- **Auto-refresh**: Periodic data updates
- **Clean UI**: Professional dashboard interface

## Purpose
- Monitor Bitcoin network in real-time
- Track price movements and market data
- Display blockchain statistics and metrics
- Provide dashboard interface for Bitcoin data
- Enable Bitcoin-aware ordinal applications
- Real-time Bitcoin price monitoring
- Blockchain statistics display
- Network health indicators
- User-friendly dashboard interface

## Key Features

### HTML Structure
The script contains a complete HTML structure for a Bitcoin monitoring dashboard:

```html
<div class="bitcoin-monitor">
    <header>
        <h1>Bitcoin Monitor</h1>
        <div class="status-indicator"></div>
    </header>
    
    <main>
        <section class="price-section">
            <!-- Price display -->
        </section>
        
        <section class="stats-section">
            <!-- Blockchain statistics -->
        </section>
        
        <section class="network-section">
            <!-- Network information -->
        </section>
    </main>
</div>
```

### Dashboard Components

#### Price Section
- Current Bitcoin price in USD
- Price change indicators (24h)
- Market cap information
- Volume statistics

#### Statistics Section
- Block height
- Difficulty adjustment data
- Mempool status
- Hash rate information

#### Network Section
- Node count
- Network health status
- Transaction throughput
- Fee recommendations

## Visual Design

### Layout
- Responsive grid layout
- Clean, modern interface
- Color-coded status indicators
- Mobile-friendly design

### Color Scheme
- Primary: Bitcoin orange (#FF9900)
- Secondary: Dark gray (#333333)
- Success: Green (#00FF00)
- Warning: Yellow (#FFFF00)
- Error: Red (#FF0000)

### Typography
- Clear, readable fonts
- Hierarchical information display
- Emphasis on important metrics
- Accessible font sizing

## Data Sources

### Price APIs
- Integration with Bitcoin price feeds
- Real-time price updates
- Historical price data
- Multi-currency support

### Blockchain APIs
- Block explorer integration
- Mempool monitoring
- Network statistics
- Node information

## Interactive Features

### Real-time Updates
- Auto-refreshing data
- WebSocket connections
- Live price feeds
- Dynamic chart updates

### User Controls
- Refresh buttons
- Time range selectors
- Currency switchers
- Theme toggles

## Usage Examples

### Basic Implementation
```javascript
import 'bitmon';

// Dashboard automatically initializes
// HTML structure is injected into page
```

### Custom Configuration
```javascript
// Configure update intervals
window.bitmonConfig = {
    priceUpdateInterval: 30000,  // 30 seconds
    statsUpdateInterval: 60000,  // 1 minute
    theme: 'dark'
};
```

### Event Handling
```javascript
// Listen for price updates
document.addEventListener('bitcoin-price-update', (event) => {
    console.log('New price:', event.detail.price);
});

// Listen for network status changes
document.addEventListener('bitcoin-network-status', (event) => {
    console.log('Network status:', event.detail.status);
});
```

## API Integration

### External Services
- CoinGecko API for price data
- Blockchain.info for statistics
- Mempool.space for network data
- Custom ordinal server endpoints

### Error Handling
- Graceful API failure handling
- Fallback data sources
- User notification system
- Retry mechanisms

## Performance Optimizations

### Data Caching
- Local storage for price history
- Cached network statistics
- Optimized API calls
- Efficient DOM updates

### Loading States
- Skeleton screens during load
- Progressive data loading
- Smooth transitions
- Loading indicators

## Responsive Design

### Mobile Support
- Touch-friendly interface
- Optimized layouts
- Swipe gestures
- Mobile-specific features

### Desktop Features
- Multi-column layouts
- Hover effects
- Keyboard navigation
- Advanced charting

## Customization Options

### Themes
- Light and dark modes
- Custom color schemes
- Brand customization
- Accessibility options

### Layout
- Configurable sections
- Widget arrangement
- Size adjustments
- Panel visibility

## Integration with Ordinals

### Recursive Endpoints
- Uses ordinal server APIs
- Integrates with Bitcoin infrastructure
- Supports ordinal-specific data
- Blockchain inscription tracking

### Bitcoin Network
- Real Bitcoin network data
- Live blockchain information
- Ordinal-compatible endpoints
- Network health monitoring

## Related Files
- `recursive-endpoints.js` - API integration
- `bitmapOCI.js` - Bitmap data access
- `index.html` - Main application structure

## Use Cases
- Bitcoin traders and investors
- Ordinal inscription creators
- Blockchain developers
- Network monitoring tools
- Educational dashboards
