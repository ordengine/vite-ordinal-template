# React Three Fiber Import Map v1.01

## Overview
Critical import map configuration that enables recursive ordinal loading for React Three Fiber applications. Maps all external dependencies to their corresponding ordinal inscription IDs for decentralized, on-chain module loading.

## Version
v1.01 - Vite Ordinal Template compatible

## Purpose
- Enable recursive ordinal imports for all dependencies
- Map npm packages to their ordinal inscription equivalents
- Support decentralized React Three Fiber applications
- Provide on-chain dependency resolution
- Defines import mappings for React Three Fiber ecosystem
- Maps library names to Bitcoin ordinal inscription IDs
- Enables ordinal-based dependency resolution
- Provides version v1.01 of the react-three-fiber importMap

## Key Features

### Core React Libraries
```javascript
"react": "/content/609b117277f1e9c9f27f358fe02db34e13d08915bbcea18770dc36f5f3afcbb2i0"
"react-dom": "/content/609b117277f1e9c9f27f358fe02db34e13d08915bbcea18770dc36f5f3afcbb2i1"
"react-dom/client": "/content/4d9308ce08bed11c028acb3d1dd964ea0e9809f51daf141ca0760e745a8070aei0"
```

### Three.js Ecosystem
```javascript
"three": "/content/0d013bb60fc5bf5a6c77da7371b07dc162ebc7d7f3af0ff3bd00ae5f0c546445i0"
"@react-three/fiber": "/content/f1be1caad667af0ec844d1333ad4d38f2cd7cc2855404bba11ac436b53c799b6i0"
"@react-three/drei": "/content/ded46f972b0f85ea041359cd94a7878a5e902126fb34ee11dbed1c9ae4dfb1ebi0"
```

### Shader & Material Composition
```javascript
"material-composer": "/content/ffffa2b0d398de68409230e9f41f6dd7748a4433d4239f328a3f886874b46aa0i4"
"shader-composer": "/content/ffffa2b0d398de68409230e9f41f6dd7748a4433d4239f328a3f886874b46aa0i1"
"vfx-composer": "/content/fffff8af34fb45dfac622a385bb6846a3c206595e6cb4daa04a7a90ed02bc833i0"
```

### State Management & ECS
```javascript
"miniplex": "/content/609b6f6f16d2efb9841357a3e161cc54f46dc12c20624696e1d613f86b36dbaai0"
"statery": "/content/c0de1c2494d23616f14ad5e55e9c9ac4dc91e3908e3de0ad13f4b9009ae20bcai2"
```

### Utilities & Helpers
```javascript
"randomish": "/content/e61e018322265768010a2a88751510e9abb0591ed49e39cc3781f44716b912f0i0"
"leva": "/content/609bad601cdafa4d4a2622bbd9f4ebfdd278b8c5ea1efeb0d468db33f871fffai2"
"maath": "/content/c0de1c2494d23616f14ad5e55e9c9ac4dc91e3908e3de0ad13f4b9009ae20bcai3"
```

### Custom Extensions
```javascript
"recursive-endpoints": "/content/89fbbeca30c87535f9db283da584006c90076f220dbf410a01985a1840e0ea0ci0"
"boxelGeometry": "/content/c0decdd785a4cfb37a4fce01f62386dec5be5e91a27bf09d121167e473b3cc9fi0"
"bitmapOCI": "/content/840bc0df4ffc5a7ccedbee35e97506c9577160e233982e627d0045d06366e362i0"
"bitmon": "/content/55551557695dd82a2bda5ec3497684ec7cbb2cc1752ff5101accff1648666c3ai0"
```

## Usage
This import map is used by the build system to resolve dependencies during the bundling process. When the application is deployed as an ordinal inscription, these paths resolve to actual inscribed content on the Bitcoin blockchain.

## Version Information
- Version: 1.01
- Template: github.com/ordengine/vite-ordinal-template
- Community: github.com/pmndrs (Poimandres)

## Related Files
- `index.html` - Contains the import map configuration
- `package.json` - Contains inscription mappings
- All recursive script files reference these mappings
