# Ordinal Dependencies Complete Overview

## ⚠️ **PROJECT GUIDELINES - BITCOIN INSCRIPTION CONSTRAINTS**

### **🎯 Core Principle: Ordinal-First Development**
This project is designed to be inscribed on the Bitcoin blockchain as a single HTML file. This creates **strict dependency constraints** that must be followed:

### **🔄 DUAL-MODE DEVELOPMENT ARCHITECTURE**

This project uses a sophisticated **dual-mode setup** that allows local development with Node.js dependencies while building for Bitcoin inscription deployment:

### **✅ ALLOWED Dependencies**
- **ONLY use libraries available in the import map from index.html** 
- **ONLY import from `/content/` URLs** (ordinal inscriptions)
- **ONLY use dependencies listed in package.json "inscriptions" section**
- **NO external URLs** (CDNs, APIs, etc.)
- **NO Node.js modules** beyond what's pre-inscribed

### **❌ FORBIDDEN Dependencies**
- ❌ NPM packages not in import map
- ❌ External CDN imports
- ❌ HTTP/HTTPS requests to external services
- ❌ Dynamic imports from non-ordinal sources
- ❌ WebAssembly modules
- ❌ Service workers or web workers
- ❌ File system access

### **📋 Development Rules**

1. **Check Import Map First**: Before adding any import, verify it exists in index.html
2. **Bitcoin-Native**: Leverage ordinal endpoints (`/content/`, `/r/blockinfo`)

### **🔍 Import Map Verification**
Before using any library, check if it exists in the import map:
```javascript
// ✅ CORRECT - Available in import map
import { Canvas } from '@react-three/fiber'
import { useControls } from 'leva'
import { Vector3 } from 'three'

// ❌ INCORRECT - Not in import map
import axios from 'axios'           // External HTTP library
import lodash from 'lodash'         // Not pre-inscribed
import './custom.css'               // External file
```

### **🛠️ Adding New Dependencies**
To add a new dependency:
1. Create ordinal inscription of the library
2. Add to `package.json` "inscriptions" section
3. Update import map in `index.html`
4. Test locally, then rebuild


## 📂 **Available Dependencies**

This project provides access to **49 JavaScript libraries** that enable ordinal-first development for React Three Fiber applications. All dependencies are available as Bitcoin inscriptions and can be imported via the import map system.

### 🔧 **Core Project Libraries (Custom Development)**
*Libraries specifically created for this ordinal template project*

| Library | Purpose | Lines | Author/Source |
|---------|---------|-------|---------------|
| `recursive-endpoints` | Ordinal data access library | 384 | Eloc |
| `bitmapOCI` | Bitcoin Bitmap On-Chain Index (0-839,999) | ~300 | @_lefrog, bop.609.bitmap, contributions |
| `bitmon` | Bitcoin network monitoring dashboard | 58 | Project custom |
| `boxelGeometry` | 3D boxel/voxel geometry generator | 126 | bop.609.bitmap |
| `ecs` | Entity Component System + canvas config | 133 | Project custom |
| `GridFloor` | Infinite grid floor R3F component | 26 | Project custom |
| `useCollider` | Collision detection hook | 47 | Project custom |
| `shaderNoiseFunctions` | GLSL noise & utility functions | 119 | Various (IQ, community) |

### ⚛️ **React Ecosystem**
*Core React libraries for ordinal applications*

| Library | Purpose | Size | Version |
|---------|---------|------|---------|
| `react` | Core React library | Large | Latest |
| `react-dom` | React DOM manipulation | Large | Latest |
| `react-dom/client` | React 18 client rendering | Large | Latest |
| `react/jsx-runtime` | JSX runtime support | Medium | Latest |

### 🎮 **Three.js & 3D Graphics**
*3D graphics and visualization libraries*

| Library | Purpose | Features |
|---------|---------|----------|
| `three` | Core Three.js library | Complete 3D engine |
| `@react-three/fiber` | React Three Fiber | React + Three.js integration |
| `@react-three/drei` | Drei helpers | 100+ R3F utilities |
| `@react-three/cannon` | Physics engine | Cannon.js physics |
| `@react-three/postprocessing` | Post-processing | Visual effects pipeline |
| `@react-three/a11y` | Accessibility | A11y for 3D scenes |
| `@react-three/csg` | CSG operations | Boolean geometry operations |
| `BufferGeometryUtils` | Geometry utilities | Three.js geometry helpers |
| `FBXLoader` | FBX model loader | 3D model importing |
| `gltfAndDraco` | GLTF + Draco loader | Compressed 3D models |
| `three-mesh-bvh` | BVH acceleration | Spatial optimization |
| `three-custom-shader-material` | Custom shaders | Advanced materials |

### 🎨 **Shader & Material Composition**
*Advanced rendering and visual effects*

| Library | Purpose | Ecosystem |
|---------|---------|-----------|
| `shader-composer` | Shader composition | hmans/composer-suite |
| `shader-composer-r3f` | R3F shader integration | hmans/composer-suite |
| `shader-composer-toybox` | Shader utilities | hmans/composer-suite |
| `material-composer` | Material composition | hmans/composer-suite |
| `material-composer-r3f` | R3F material integration | hmans/composer-suite |
| `vfx-composer` | VFX composition | hmans/composer-suite |
| `vfx-composer-r3f` | R3F VFX integration | hmans/composer-suite |
| `boxels-shader` | Custom boxel shaders | Project-specific |

### 🎭 **Animation & Interaction**
*Animation libraries and user interaction*

| Library | Purpose | Features |
|---------|---------|----------|
| `@react-spring/three` | 3D animations | Spring-based animations |
| `@react-spring/web` | Web animations | DOM animations |
| `@use-gesture/react` | Gesture handling | Touch/mouse interactions |
| `@pixiv/three-vrm` | VRM support | Virtual character models |

### 🏗️ **State Management & Architecture**
*Application architecture and data flow*

| Library | Purpose | Paradigm |
|---------|---------|----------|
| `miniplex` | ECS world management | Entity Component System |
| `miniplex-react` | React ECS integration | ECS + React hooks |
| `statery` | Global state | Reactive state management |
| `suspend-react` | Async components | React Suspense utilities |

### 🎚️ **Development & Debugging**
*Development tools and performance monitoring*

| Library | Purpose | Features |
|---------|---------|----------|
| `leva` | GUI controls | ~9337 lines, Debug GUI |
| `r3f-perf` | Performance monitoring | R3F performance stats |

### 🎲 **Math & Utilities**
*Mathematical functions and utility libraries*

| Library | Purpose | Features |
|---------|---------|----------|
| `maath` | Math utilities | pmndrs math library |
| `alea` | PRNG | Alea random number generator |
| `simplex-noise` | Noise generation | Simplex noise algorithm |
| `randomish` | Random utilities | hmans randomish library |

---

## 📊 **Statistics Summary**

### **By Category:**
- **Custom Project Files**: 10 files
- **React Ecosystem**: 5 files  
- **Three.js & 3D**: 12 files
- **Shader/Material Composition**: 8 files
- **Animation & Interaction**: 4 files
- **State Management**: 4 files
- **Development Tools**: 2 files
- **Math & Utilities**: 4 files
- **Babel Tools**: 1 file
- **Assets**: 1 file

### **By Source:**
- **pmndrs ecosystem**: ~15 files (React Three Fiber, Drei, etc.)
- **hmans composer-suite**: 8 files (shader/material/vfx composers)
- **Custom development**: 10 files (project-specific)
- **External libraries**: ~16 files (Three.js, React, utilities)

### **By Size (Estimated):**
- **Large files (>1000 lines)**: React, Three.js, Leva, Maath
- **Medium files (100-1000 lines)**: Most R3F ecosystem files
- **Small files (<100 lines)**: Custom project files, utilities

---

## 🎯 **Key Features Enabled**

### **Bitcoin Integration**
- Real-time Bitcoin price monitoring (`bitmon.js`)
- Complete bitmap inscription index (`bitmapOCI.js`) 
- Ordinal data querying (`recursive-endpoints.js`)

### **3D Graphics Capabilities**
- Complete Three.js 3D engine
- React Three Fiber integration
- 100+ ready-to-use 3D components (Drei)
- Physics simulation (Cannon.js)
- Post-processing effects
- VR/AR support potential

### **Advanced Rendering**
- Custom shader composition
- Material authoring tools
- Visual effects pipeline
- Procedural generation
- Noise functions for shaders

### **Development Experience**
- Entity Component System architecture
- Hot reloading and debugging
- Performance monitoring
- GUI controls for tweaking
- State management patterns

### **Animation & Interaction**
- Spring-based animations
- Gesture handling
- Touch/mouse interactions
- Smooth camera controls

---

## 🔄 **Ordinal-First Architecture**

### **Import Map Resolution**
All dependencies resolve through `script1.js` import map to ordinal inscriptions:
```javascript
"three": "/content/0d013bb60fc5bf5a6c77da7371b07dc162ebc7d7f3af0ff3bd00ae5f0c546445i0"
"react": "/content/609b117277f1e9c9f27f358fe02db34e13d08915bbcea18770dc36f5f3afcbb2i0"
```

### **Decentralized Dependencies**
- **No NPM required**: All packages are Bitcoin inscriptions
- **Immutable**: Dependencies can't be changed or removed
- **Censorship resistant**: Hosted on Bitcoin blockchain
- **Version locked**: Specific inscription IDs ensure consistency

### **Local Development**
- Files cached locally for development speed
- Production loads directly from ordinal servers
- Recursive loading enables complex dependency trees

---

## 🚀 **Usage Patterns**

### **Basic 3D Scene**
```javascript
import { Canvas } from '@react-three/fiber'
import { boxelGeometry5 } from 'boxelGeometry'
import GridFloor from 'GridFloor'
import {CameraControls} from "@react-three/drei";
// First-person shooter style
import {PointerLockControls} from "@react-three/drei"
<PointerLockControls />
// Object manipulation
import {TransformControls} from "@react-three/drei"
<TransformControls object={meshRef} />
// Scroll-based movement
import {ScrollControls} from "@react-three/drei"
<ScrollControls pages={3}>
  <Scene />
</ScrollControls>

```

### **Bitcoin Data Integration**
```javascript
import { getBitmapSatsRange } from 'bitmapOCI'
import { getInscription } from 'recursive-endpoints'
import { fetchBitcoinPrice } from 'bitmon'
```

### **Advanced Composition**
```javascript
import { ECS, useSystem } from 'ecs'
import { ShaderComposer } from 'shader-composer-r3f'
import { useControls } from 'leva'
```

---

## 🚨 **BEST PRACTICES & TROUBLESHOOTING**

### **✅ Development Best Practices**

1. **Always Test Build**: `npm run build` frequently to catch inscription issues early
2. **Size Monitoring**: Keep an eye on final HTML file size (affects inscription cost)
3. **Dependency Validation**: Verify all imports resolve during build process
4. **Offline Testing**: Test built HTML file without internet connection
5. **Ordinal Compatibility**: Ensure all `/content/` references work on ordinals.com

### **🔧 Common Issues & Solutions**

#### **Import Errors**
```bash
# Error: Module not found
❌ import something from 'unknown-package'
✅ import something from 'package-in-import-map'
```

#### **Build Failures**
```bash
# Check these when build fails:
1. All imports exist in script1.js import map
2. No external HTTP requests in code  
3. No dynamic imports outside ordinal system
4. No Node.js specific APIs used
```

#### **Runtime Errors**
```bash
# If ordinal doesn't work:
1. Check browser console for 404s on /content/ URLs
2. Verify all inscription IDs are valid
3. Test on ordinals.com/content/your-id
4. Ensure no CORS issues with ordinal server
```

### **📏 Size Optimization Tips**

1. **Tree Shaking**: Only import what you need from large libraries
2. **Shader Optimization**: Use compressed GLSL when possible
3. **Asset Inlining**: Keep assets as small ordinal inscriptions
4. **Code Splitting**: Use React.lazy() for optional components
5. **Build Analysis**: Check `build/index.html` for bloated dependencies

### **🔗 Ordinal Integration Patterns**

```javascript
// ✅ Proper ordinal data fetching
import { getInscription } from 'recursive-endpoints'
const data = await getInscription('abc123...i0')

// ✅ Bitcoin blockchain queries  
import { getBitmapSatsRange } from 'bitmapOCI'
const sats = getBitmapSatsRange(609)

// ✅ Recursive inscription loading
import Component from '/content/def456...i0'
```

This architecture enables building sophisticated, Bitcoin-native 3D applications that are completely decentralized and censorship-resistant while providing a modern development experience.

---

## 🔄 DUAL-MODE DEVELOPMENT ARCHITECTURE

This project uses a sophisticated **dual-mode setup** that allows local development with Node.js dependencies while building for Bitcoin inscription deployment:

#### **🏠 Local Development Mode (`npm run dev`)**
- **Uses Node.js modules** from `package.json` dependencies
- **Proxies `/content/` requests** to `ordinals.com` for testing
- **Hot module replacement** for rapid development
- **Import map active** in `index.html` for module resolution
- **Local caching** of ordinal inscriptions in `node_modules/cached_inscriptions/`

#### **🪙 Production Build Mode (`npm run build`)**
- **Bundles to single HTML file** using `vite-plugin-singlefile`
- **Replaces module aliases** with ordinal content URLs
- **Removes import map** from final HTML
- **External dependencies** marked in Rollup config
- **Post-build replacement** converts identifiers to `/content/` URLs

#### **⚙️ Vite Configuration Magic**

```javascript
// Dynamic alias resolution based on build mode
let aliases = {}
Object.keys(externalModules).forEach(name => {
    aliases[name] = isProduction
        ? ('https://ordinals.com/content/' + externalModules[name])  // Production: Direct ordinal URLs
        : path.resolve(__dirname, 'external_modules/content/' + externalModules[name])  // Dev: Local files
})

// Development proxy for ordinal content
server: {
    proxy: {
        '/content': {
            target: 'https://ordinals.com',
            changeOrigin: true,
        }
    }
}

// Production: Mark dependencies as external for ordinal loading
build: {
    rollupOptions: {
        external: ['three', 'react', '@react-three/fiber', /* ...all ordinal deps */]
    }
}
```

#### **📁 Dependency Resolution Strategy**

**Development:**
1. Use Node.js modules from `package.json` dependencies
2. Cache ordinal content locally in `node_modules/cached_inscriptions/`
3. Proxy `/content/` requests to ordinals.com for testing
4. Use import map for module resolution

**Production:**
1. Bundle application code only
2. Mark all dependencies as external
3. Replace import identifiers with `/content/` URLs
4. Remove import map from final HTML
5. Result: Self-contained ordinal inscription

#### **🔄 Caching System**
```javascript
// Auto-downloads and caches ordinal inscriptions locally
async load(id) {
    try {
        return await fs.readFile(cachedFilePath, 'utf-8');  // Use cache if exists
    } catch (err) {
        const fileUrl = `https://ordinals.com/content/${fileName}`;
        const content = await fetch(fileUrl);               // Download if missing
        await fs.writeFile(cachedFilePath, content);        // Cache for next time
        return content;
    }
}
```

This architecture ensures **seamless development experience** while maintaining **Bitcoin inscription compatibility**.

#### **📋 Package.json Inscriptions Mapping**

The `package.json` contains two key sections for dual-mode operation:

```json
{
  "dependencies": {
    "@react-three/fiber": "^8.17.10",    // Local development versions
    "@react-three/drei": "^9.114.3",
    "three": "^0.169.0"
  },
  "inscriptions": {
    "GridFloor": "/content/c0ded73640f3a5094b2ebf32d18625005a00271cd42ee7fa62f6c6f61f97bbc3i0",
    "boxelGeometry": "/content/c0decdd785a4cfb37a4fce01f62386dec5be5e91a27bf09d121167e473b3cc9fi0",
    "bitmapOCI": "/content/840bc0df4ffc5a7ccedbee35e97506c9577160e233982e627d0045d06366e362i0"
  }
}
```

**Development:** Uses `dependencies` with standard npm packages  
**Production:** Uses `inscriptions` mapping to ordinal content URLs

#### **🔄 Build Process Flow**

1. **`npm install`** - Downloads Node.js dependencies for development
2. **`npm run dev`** - Starts Vite dev server with proxy and caching
3. **`npm run build`** - Creates ordinal-compatible single HTML file
4. **Upload to Bitcoin** - Inscribe the `build/index.html` file

---

### **✅ ALLOWED Dependencies**
