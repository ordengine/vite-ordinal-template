# useCollider.js - Collision System for Player Controllers

## Overview
Collision detection system specifically designed for BasicPlayerController integration. Provides vertical collision detection for meshes and groups, with global collider state management using Statery.

## Dependencies
- **React**: useEffect hook
- **@react-three/fiber**: useThree hook
- **statery**: Global state management

## Purpose
- Add vertical collision to 3D objects
- Global collider registry and management
- Integration with player controller systems
- Dynamic collider addition/removal
- Provides collision detection for mesh objects
- Integrates with camera controls for player movement
- Manages collider registration and cleanup
- Enables physics-based interactions

## Key Features

### Collider Store
```javascript
export const colliderStore = makeStore({ colliders: {} });
```
- Global store for managing all colliders
- Efficient collider lookup and management
- Automatic cleanup and memory management

### Core Functions

#### `addCollider(objectOrArray, name)`
Adds an object or array of objects to the collider system.
```javascript
export const addCollider = (objectOrArray, name) => {
    const obj = { ...colliderStore.state.colliders };
    obj[name || Math.random()] = objectOrArray;
    colliderStore.set({ colliders: obj });
};
```

#### `removeCollider(name)`
Removes a collider from the system.
```javascript
export const removeCollider = (name) => {
    const obj = { ...colliderStore.state.colliders };
    delete obj[name];
    colliderStore.set({ colliders: obj });
};
```

### Main Hook: `useCollider(ref, name, camera)`
```javascript
export const useCollider = (ref, name, camera) => {
    const { controls } = useThree();
    // Automatic registration and cleanup logic
};
```

## Parameters
- **ref**: React ref to the mesh or group object
- **name**: Optional unique identifier for the collider
- **camera**: Boolean flag to integrate with camera controls

## Usage Examples

### Basic Collision Detection
```javascript
import { useCollider } from 'useCollider';
import { useRef } from 'react';

function CollisionBox() {
    const boxRef = useRef();
    
    useCollider(boxRef, 'collision-box');
    
    return (
        <mesh ref={boxRef}>
            <boxGeometry args={[2, 2, 2]} />
            <meshStandardMaterial color="red" />
        </mesh>
    );
}
```

### Camera Collision Integration
```javascript
function Wall() {
    const wallRef = useRef();
    
    // Enable camera collision with this wall
    useCollider(wallRef, 'wall-1', true);
    
    return (
        <mesh ref={wallRef}>
            <boxGeometry args={[10, 5, 1]} />
            <meshStandardMaterial color="gray" />
        </mesh>
    );
}
```

### Multiple Colliders
```javascript
function Level() {
    const platform1Ref = useRef();
    const platform2Ref = useRef();
    
    useCollider(platform1Ref, 'platform-1', true);
    useCollider(platform2Ref, 'platform-2', true);
    
    return (
        <>
            <mesh ref={platform1Ref} position={[0, 0, 0]}>
                <boxGeometry args={[5, 1, 5]} />
                <meshStandardMaterial color="green" />
            </mesh>
            <mesh ref={platform2Ref} position={[10, 2, 0]}>
                <boxGeometry args={[5, 1, 5]} />
                <meshStandardMaterial color="blue" />
            </mesh>
        </>
    );
}
```

### Dynamic Collider Management
```javascript
function DynamicCollider({ active }) {
    const objectRef = useRef();
    
    // Only add collider when active
    if (active) {
        useCollider(objectRef, 'dynamic-collider');
    }
    
    return (
        <mesh ref={objectRef}>
            <sphereGeometry args={[1]} />
            <meshStandardMaterial color={active ? "red" : "gray"} />
        </mesh>
    );
}
```

## Integration with Controls
When `camera` parameter is `true`:
- Adds mesh to control system's `colliderMeshes` array
- Enables automatic collision detection during camera movement
- Provides vertical collision for player controllers

## Lifecycle Management
- Automatic registration on component mount
- Automatic cleanup on component unmount
- Memory leak prevention
- Efficient re-registration on dependency changes

## Dependencies
- `statery` - State management for collider store
- `@react-three/fiber` - React Three Fiber integration
- React hooks for lifecycle management

## Performance Considerations
- Efficient collider lookup using object keys
- Minimal re-renders through proper dependency management
- Optimized for real-time collision detection
- Suitable for complex scenes with many colliders

## Related Files
- `ecs.js` - Entity Component System integration
- `statery.js` - State management library
- `@react-three_fiber.js` - React Three Fiber core

## Use Cases
- First-person camera controls
- Platform games
- Architectural walkthroughs
- Interactive 3D environments
- Physics simulations
