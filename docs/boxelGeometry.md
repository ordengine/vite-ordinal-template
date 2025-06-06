# boxelGeometry.js - 3D Boxel Geometry Generator

## Overview
Custom Three.js geometry generator for creating boxel (3D pixel/voxel) shapes with variable faceting. Creates rounded cube geometries with chamfered edges for 3D pixel art and voxel-based applications.

## Author
**bop.609.bitmap**
bop.609.bitmap

## Purpose
- Creates custom 3D geometry for voxel-style objects
- Provides chamfered/rounded edges for softer appearance
- Optimized for procedural generation and voxel art
- Compatible with Three.js BufferGeometry system

## Key Features

### Facet Customization
```javascript
const makeGeometry = (facet) => {
    // facet parameter controls edge chamfering
    let f = facet * 0.05; // Facet scaling factor
}
```

### Geometry Properties
- Default dimensions: 1x1x1 unit cube
- Chamfered edges based on facet parameter
- Optimized vertex layout
- Proper face indexing for efficient rendering

### Vertex Generation
The geometry creates vertices for 6 faces with chamfered edges:
- **Positive X face** (right)
- **Positive Z face** (front) 
- **Negative X face** (left)
- **Negative Z face** (back)
- **Positive Y face** (top)
- **Negative Y face** (bottom)

## Technical Implementation

### Vertex Layout
```javascript
let vertices = new Float32Array([
    // px (positive X face)
    hw, hh - f, -hd + f,   // Chamfered corner vertices
    hw, -hh + f, -hd + f,
    // ... additional vertices for all faces
]);
```

### Face Indexing
- Uses proper winding order for correct normals
- Optimized triangle indexing
- Supports both solid and wireframe rendering

### Buffer Attributes
- Position buffer with chamfered vertices
- Normal calculation for proper lighting
- UV coordinates for texture mapping

## Usage Examples

### Basic Boxel Creation
```javascript
import { makeGeometry } from 'boxelGeometry';

// Create geometry with moderate chamfering
const geometry = makeGeometry(0.2);
const material = new THREE.MeshStandardMaterial({ color: 0x00ff00 });
const boxel = new THREE.Mesh(geometry, material);
scene.add(boxel);
```

### Varying Facet Values
```javascript
// Sharp edges (minimal chamfering)
const sharpBoxel = makeGeometry(0.0);

// Soft edges (heavy chamfering)
const softBoxel = makeGeometry(1.0);

// Balanced appearance
const balancedBoxel = makeGeometry(0.5);
```

### Procedural Generation
```javascript
// Create a grid of varied boxels
for (let x = 0; x < 10; x++) {
    for (let z = 0; z < 10; z++) {
        const facet = Math.random();
        const geometry = makeGeometry(facet);
        const boxel = new THREE.Mesh(geometry, material);
        boxel.position.set(x, 0, z);
        scene.add(boxel);
    }
}
```

## Performance Considerations
- Efficient vertex generation
- Optimized for batch creation
- Suitable for instanced rendering
- Memory-efficient geometry data

## Integration
- Compatible with React Three Fiber
- Works with standard Three.js materials
- Supports physics engines (Cannon, etc.)
- Ideal for voxel-based games and art

## Related Files
- `boxels-shader.js` - Custom shader for boxel rendering
- `GridFloor.js` - Grid system for boxel placement
- `three.js` - Three.js core library
- `BufferGeometryUtils.js` - Geometry utilities

## Applications
- Voxel art and games
- Procedural generation
- Architectural visualization
- Abstract 3D compositions
