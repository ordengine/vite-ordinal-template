# shaderNoiseFunctions.js - GLSL Noise & Utility Functions

## Overview
Comprehensive collection of GLSL shader functions including noise algorithms, color space conversion, border detection, and utility functions. Features implementations from industry experts like Inigo Quilez.

## Key Contributors
- **Inigo Quilez**: iqnoise implementation (MIT License)
- **Stefan Gustavson**: Simplex noise implementation
- **Community**: Various shader utility functions

## Purpose
- Provide production-ready GLSL noise functions
- Color space conversion utilities (sRGB ↔ Linear)
- UI border and edge detection for shaders
- Procedural generation building blocks
- Custom material development support
- Provides reusable GLSL shader code snippets
- Enables procedural noise generation in shaders
- Offers color space conversion utilities
- Includes UI border detection functions

## Exported Functions

### `oldShaderNoise`
Classic 2D noise implementation with smooth interpolation.

```glsl
float random (in vec2 st) {
    return fract(sin(dot(st.xy,vec2(12.9898,78.233))) * 43758.5453123);
}

float snoise (in vec2 st) {
    vec2 i = floor(st);
    vec2 f = fract(st);
    
    float a = random(i);
    float b = random(i + vec2(1.0, 0.0));
    float c = random(i + vec2(0.0, 1.0));
    float d = random(i + vec2(1.0, 1.0));
    
    vec2 u = f*f*(3.0-2.0*f);
    
    return mix(a, b, u.x) + (c - a) * u.y * (1.0 - u.x) + (d - b) * u.x * u.y;
}
```

### `toLinear`
sRGB to linear color space conversion.

```glsl
vec4 toLinear(vec4 sRGB) {
    vec3 higher = pow((sRGB.rgb + vec3(0.055)) / vec3(1.055), vec3(2.4));
    vec3 lower = sRGB.rgb / vec3(12.92);

    vec3 linearRGB = vec3(
        sRGB.r < 0.04045 ? lower.r : higher.r,
        sRGB.g < 0.04045 ? lower.g : higher.g,
        sRGB.b < 0.04045 ? lower.b : higher.b
    );

    return vec4(linearRGB, sRGB.a);
}
```

### `isInBorder`
UI border detection for creating frame effects.

```glsl
bool isInBorder(vec2 uv, float startUV, float thickness, float extra) {
    float stopUV = 1. - startUV;
    bool isInHorizontal = (uv.x > startUV - extra && uv.x < stopUV + extra);
    bool isInVertical = (uv.y > startUV - extra && uv.y < stopUV + extra);

    bool topEdge = isInHorizontal && (abs(uv.y - startUV) < thickness);
    bool bottomEdge = isInHorizontal && (abs(uv.y - stopUV) < thickness);
    bool leftEdge = isInVertical && (abs(uv.x - startUV) < thickness);
    bool rightEdge = isInVertical && (abs(uv.x - stopUV) < thickness);

    return topEdge || bottomEdge || leftEdge || rightEdge;
}
```

## Usage Examples

### Basic Noise Shader
```javascript
import { oldShaderNoise } from 'shaderNoiseFunctions';

const noiseShader = new THREE.ShaderMaterial({
    fragmentShader: `
        ${oldShaderNoise}
        
        varying vec2 vUv;
        
        void main() {
            float noise = snoise(vUv * 10.0);
            gl_FragColor = vec4(vec3(noise), 1.0);
        }
    `,
    // ... other shader properties
});
```

### Color Space Conversion
```javascript
import { toLinear } from 'shaderNoiseFunctions';

const colorShader = new THREE.ShaderMaterial({
    fragmentShader: `
        ${toLinear}
        
        uniform vec4 color;
        
        void main() {
            vec4 linearColor = toLinear(color);
            gl_FragColor = linearColor;
        }
    `,
    uniforms: {
        color: { value: new THREE.Vector4(0.5, 0.7, 0.9, 1.0) }
    }
});
```

### UI Border Effects
```javascript
import { isInBorder } from 'shaderNoiseFunctions';

const borderShader = new THREE.ShaderMaterial({
    fragmentShader: `
        ${isInBorder}
        
        varying vec2 vUv;
        uniform vec3 borderColor;
        uniform vec3 fillColor;
        
        void main() {
            bool border = isInBorder(vUv, 0.1, 0.02, 0.0);
            vec3 color = border ? borderColor : fillColor;
            gl_FragColor = vec4(color, 1.0);
        }
    `,
    uniforms: {
        borderColor: { value: new THREE.Vector3(1.0, 0.0, 0.0) },
        fillColor: { value: new THREE.Vector3(0.0, 0.0, 1.0) }
    }
});
```

### Combined Effects
```javascript
import { oldShaderNoise, toLinear, isInBorder } from 'shaderNoiseFunctions';

const complexShader = new THREE.ShaderMaterial({
    fragmentShader: `
        ${oldShaderNoise}
        ${toLinear}
        ${isInBorder}
        
        varying vec2 vUv;
        uniform float time;
        
        void main() {
            // Animated noise
            float noise = snoise(vUv * 5.0 + time * 0.1);
            
            // Base color with noise
            vec4 baseColor = vec4(0.5 + noise * 0.3, 0.3, 0.8, 1.0);
            
            // Convert to linear space
            vec4 linearColor = toLinear(baseColor);
            
            // Add border
            bool border = isInBorder(vUv, 0.05, 0.01, 0.0);
            if (border) {
                linearColor.rgb = vec3(1.0, 1.0, 0.0);
            }
            
            gl_FragColor = linearColor;
        }
    `,
    uniforms: {
        time: { value: 0.0 }
    }
});
```

## Function Details

### Noise Generation
- **Random function**: Pseudo-random number generation from 2D coordinates
- **Smooth noise**: Interpolated noise with smooth transitions
- **Fractal patterns**: Suitable for creating organic textures

### Color Management
- **sRGB conversion**: Proper color space handling for realistic rendering
- **Gamma correction**: Ensures accurate color representation
- **Linear workflow**: Compatible with PBR rendering pipelines

### UI Utilities
- **Border detection**: Creates frame and outline effects
- **Edge detection**: Useful for UI highlighting
- **Thickness control**: Adjustable border width

## Performance Considerations
- Optimized GLSL code for GPU execution
- Minimal computational overhead
- Suitable for real-time rendering
- Compatible with mobile devices

## Integration
- Works with Three.js ShaderMaterial
- Compatible with React Three Fiber
- Integrates with shader-composer system
- Suitable for custom material creation

## Related Files
- `shader-composer.js` - Shader composition system
- `material-composer.js` - Material creation tools
- `three-custom-shader-material.js` - Custom shader materials
- `boxels-shader.js` - Specialized boxel shaders
