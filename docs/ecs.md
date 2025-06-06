# ecs.js - Entity Component System & Canvas Configuration

## Overview
Complete ECS (Entity Component System) setup using Miniplex and Statery, with React Three Fiber canvas defaults and global state management for systems and GUI components.

## Core Dependencies
- **Miniplex**: ECS world and React API
- **Statery**: Global state management
- **React**: Component system and hooks

## Purpose
- Entity Component System architecture
- Canvas configuration defaults
- Global system registration and management  
- GUI component state management
- Performance-optimized 3D rendering setup
- Implements ECS pattern for React Three Fiber applications
- Provides camera defaults and configuration
- Sets up global system store and GUI management
- Enables efficient component-based architecture

## Key Features

### Canvas Defaults
```javascript
export const CANVAS_DEFAULTS = {
    shadows: true,
    dpr: 1,
    camera: {
        fov: 32,
        position: [11, 2, 0],
        near: 0.1,
        far: 100000
    },
    gl: {
        preserveDrawingBuffer: false,
        powerPreference: 'high-performance',
        stencil: false,
        depth: false,
        antialias: false,
        alpha: false
    }
};
```

### ECS World Setup
- Creates a Miniplex world instance
- Provides React API for ECS operations
- Manages entities, components, and systems

### System Management
```javascript
export const systemStore = makeStore({
    systemArray: []
});

export const useSystem = system => {
    const id = useMemo(() => generateSystemId(), []);
    const ref = useRef(null);
    // System registration and cleanup logic
};
```

### GUI Store
```javascript
export const guiStore = makeStore({
    guiArray: []
});

export const useGUI = gui => {
    // GUI component management
};
```

## Core Components

### ECS World
- Central entity management
- Component registration
- System execution
- Query optimization

### System Hooks
- `useSystem()` - Register and manage systems
- `useGUI()` - GUI component integration
- Automatic cleanup and lifecycle management

### Camera Configuration
- Optimized camera settings for 3D scenes
- Performance-focused GL context
- Shadow rendering support

## Usage Examples

### Using ECS Components
```javascript
import { ECS } from 'ecs';

function MyComponent() {
    return (
        <ECS.Entity>
            <ECS.Component name="position" data={{ x: 0, y: 0, z: 0 }} />
            <ECS.Component name="velocity" data={{ x: 1, y: 0, z: 0 }} />
        </ECS.Entity>
    );
}
```

### Creating Systems
```javascript
import { useSystem } from 'ecs';

function MovementSystem() {
    useSystem((world) => {
        world.query('position', 'velocity').forEach((entity) => {
            // Update entity positions based on velocity
        });
    });
    return null;
}
```

### Canvas Setup
```javascript
import { CANVAS_DEFAULTS } from 'ecs';

<Canvas {...CANVAS_DEFAULTS}>
    {/* 3D scene content */}
</Canvas>
```

## Performance Optimizations
- High-performance GPU preferences
- Disabled unnecessary GL features
- Efficient entity querying
- Minimal re-renders

## Dependencies
- Miniplex - ECS library
- Miniplex React - React integration
- Statery - State management
- React hooks for lifecycle management

## Integration
- Works seamlessly with React Three Fiber
- Compatible with GUI systems
- Supports complex 3D applications
- Enables modular component architecture

## Related Files
- `miniplex.js` - Core ECS library
- `miniplex-react.js` - React integration
- `statery.js` - State management
- `leva.js` - GUI controls
