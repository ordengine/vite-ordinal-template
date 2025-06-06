# GridFloor.js - Infinite Grid Floor Component

## Overview
Simple React Three Fiber component that renders an infinite grid floor using `@react-three/drei`'s Grid component. Provides a professional-looking floor grid with customizable colors and fade effects.

## Dependencies
- `@react-three/drei` - Grid component
- `react/jsx-runtime` - JSX support

## Purpose
- Create infinite grid floors for 3D scenes
- Provide visual reference for 3D navigation
- Enhance spatial awareness in 3D environments
- Offer customizable grid appearance
- Provides visual reference plane for 3D scenes
- Creates infinite grid with smooth fade-out effects
- Offers extensive customization options
- Enhances spatial awareness in 3D environments

## Key Features

### Default Configuration
```javascript
const config = {
    gridSize: [10.5, 10.5],        // Grid dimensions
    cellSize: 0.1,                 // Individual cell size
    cellThickness: 1,              // Cell line thickness
    cellColor: '#6f6f6f',          // Cell line color
    sectionSize: 1,                // Major section size
    sectionThickness: 1.5,         // Major section thickness
    sectionColor: '#ff6600',       // Major section color (orange)
    fadeDistance: 100,             // Distance for fade effect
    fadeStrength: 60,              // Fade intensity
    followCamera: true,            // Follow camera movement
    infiniteGrid: true,            // Enable infinite grid
    ...props                       // Override with custom props
};
```

### Visual Properties
- **Cell Grid**: Fine grid lines for detailed reference
- **Section Grid**: Major grid lines for larger scale reference
- **Color Coding**: Different colors for cells vs sections
- **Fade Effects**: Smooth distance-based fading

### Positioning
- Default position: `[0, -0.5, 0]` (slightly below ground level)
- Configurable via props
- Supports dynamic repositioning

## Usage Examples

### Basic Grid Floor
```javascript
import GridFloor from 'GridFloor';

function Scene() {
    return (
        <>
            <GridFloor />
            {/* Other 3D objects */}
        </>
    );
}
```

### Custom Configuration
```javascript
<GridFloor
    cellColor="#333333"
    sectionColor="#ffffff"
    fadeDistance={50}
    gridSize={[20, 20]}
    position={[0, 0, 0]}
/>
```

### Dynamic Grid
```javascript
const [gridConfig, setGridConfig] = useState({
    cellSize: 0.1,
    fadeDistance: 100
});

<GridFloor {...gridConfig} />
```

## Customization Options

### Colors
- `cellColor`: Fine grid line color
- `sectionColor`: Major grid line color
- Supports hex colors, CSS color names, RGB values

### Sizing
- `gridSize`: Overall grid dimensions [width, height]
- `cellSize`: Individual cell size
- `sectionSize`: Major section size

### Visual Effects
- `fadeDistance`: Distance at which fading begins
- `fadeStrength`: Intensity of fade effect
- `cellThickness`: Line thickness for cells
- `sectionThickness`: Line thickness for sections

### Behavior
- `followCamera`: Grid follows camera movement
- `infiniteGrid`: Enables infinite grid extension

## Integration with @react-three/drei
Uses the `Grid` component from @react-three/drei:
```javascript
import { Grid } from '@react-three/drei';
```

## Performance Considerations
- Optimized rendering for infinite grids
- Efficient fade calculations
- Minimal performance impact
- Suitable for real-time applications

## Use Cases
- 3D scene navigation reference
- Architectural visualization
- Game development
- CAD applications
- Virtual reality environments

## Related Files
- `@react-three_drei.js` - Contains Grid component
- `@react-three_fiber.js` - React Three Fiber integration
- `three.js` - Three.js core library

## Styling Tips
- Use contrasting colors for better visibility
- Adjust fade distance based on scene scale
- Consider section colors for major landmarks
- Balance grid density with scene complexity
