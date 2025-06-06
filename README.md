# Vite Ordinal Template

A sophisticated **Bitcoin Ordinal Inscription Development Template** using `Vite` + `React` + `Three.js` + `React Three Fiber` + `Composer Suite` for creating interactive 3D applications that can be inscribed on the Bitcoin blockchain as single HTML files.

## 🎯 **What is this?**

This template enables you to build modern React Three Fiber applications that:
- ✅ **Deploy as Bitcoin inscriptions** (single HTML file)
- ✅ **Use 49+ JavaScript libraries** from ordinal inscriptions
- ✅ **Leverage recursive endpoints** (`/content/`, `/r/blockinfo`)
- ✅ **Maintain modern development experience** (hot reload, debugging)
- ✅ **Zero external dependencies** in production (fully decentralized)

## 🚀 **Quick Start**

### Prerequisites
- Node.js 16+ 
- Git

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ordengine/vite-ordinal-template.git
   cd vite-ordinal-template
   ```

2. **Install dependencies** (⚠️ **IMPORTANT**: Use legacy peer deps flag)
   ```bash
   npm install --legacy-peer-deps
   ```
   > **Why `--legacy-peer-deps`?** This project uses specific versions of React Three Fiber ecosystem packages that require legacy peer dependency resolution for compatibility.

3. option 1

 **Start development server**
   ```bash
   npm run dev
   ```
Option 2
**Build for Bitcoin inscription**
   ```bash
   npm run build
   ```
   Your app will be bundled into a single HTML file in the `build/` folder, ready for Bitcoin inscription.

## 🔄 **Dual-Mode Architecture**

This template uses a **sophisticated dual-mode system**:

### 🏠 **Development Mode** (`npm run dev`)
- Uses Node.js modules from `package.json`
- Proxies `/content/` requests to `ordinals.com`
- Hot module replacement & debugging tools
- Local caching of ordinal inscriptions

### 🪙 **Production Mode** (`npm run build`)
- Bundles to single HTML file 
- Replaces imports with `/content/` URLs
- Removes import map from final HTML
- Creates self-contained Bitcoin inscription

## 📦 **Available Libraries**

**49 JavaScript libraries** available as Bitcoin inscriptions:

### 🔧 **Core Project Libraries**
- `recursive-endpoints` - Ordinal data access
- `bitmapOCI` - Bitcoin Bitmap index (0-839,999)
- `bitmon` - Bitcoin network monitoring
- `boxelGeometry` - 3D boxel/voxel generator
- `GridFloor` - Infinite grid floor component
- `ecs` - Entity Component System

### ⚛️ **React Ecosystem**
- `react`, `react-dom`, `react-dom/client`
- `@react-spring/three`, `@react-spring/web`
- `@use-gesture/react`

### 🎮 **Three.js & 3D Graphics**
- `three` - Core Three.js library
- `@react-three/fiber` - React Three Fiber
- `@react-three/drei` - 100+ R3F utilities
- `@react-three/cannon` - Physics engine
- `@react-three/postprocessing` - Visual effects

### 🎨 **Shader & Material Composition**
- `shader-composer` suite (8 libraries)
- `material-composer` suite
- `vfx-composer` suite

**[View complete library list →](docs/recursive-scripts-overview.md)**

## 💡 **Using Existing Inscriptions**

Add ordinal inscriptions to your project:

1. **Add to `package.json` inscriptions section:**
   ```json
   {
     "inscriptions": {
       "MyLibrary": "/content/abc123...i0"
     }
   }
   ```

2. **Import and use:**
   ```javascript
   import { MyComponent } from 'MyLibrary'
   ```

## 🏗️ **Project Structure**

```
vite-ordinal-template/
├── src/                    # Your React application
│   ├── App.jsx            # Main app component  
│   ├── components/        # React components
│   └── config/            # Configuration files
├── docs/                  # Complete documentation
├── build/                 # Production build output
├── package.json           # Dependencies & inscriptions
├── vite.config.js         # Dual-mode Vite configuration
└── index.html             # Development import map
```

## 📚 **Documentation**

- **[Complete Ordinal Dependencies Guide](docs/recursive-scripts-overview.md)** - Comprehensive overview of all 49 libraries
- **[Individual Library Docs](docs/)** - Detailed documentation for each library
- **[Bitcoin Inscription Constraints](docs/recursive-scripts-overview.md#project-guidelines---bitcoin-inscription-constraints)** - Development rules and best practices

## 🎯 **Example Usage**

### Basic 3D Scene
```javascript
import { Canvas } from '@react-three/fiber'
import { CameraControls } from '@react-three/drei'
import GridFloor from 'GridFloor'
import { boxelGeometry5 } from 'boxelGeometry'

function App() {
  return (
    <Canvas>
      <CameraControls />
      <GridFloor />
      <mesh geometry={boxelGeometry5}>
        <meshStandardMaterial color="orange" />
      </mesh>
    </Canvas>
  )
}
```

### Bitcoin Data Integration
```javascript
import { getBitmapSatsRange } from 'bitmapOCI'
import { getInscription } from 'recursive-endpoints'
import { fetchBitcoinPrice } from 'bitmon'

// Get bitmap data
const sats = getBitmapSatsRange(609)

// Fetch inscription data
const data = await getInscription('abc123...i0')

// Monitor Bitcoin price
const price = await fetchBitcoinPrice()
```

## ⚠️ **Development Constraints**

Since this builds for Bitcoin inscription deployment:

### ✅ **ALLOWED**
- Libraries from the import map only
- `/content/` URLs (ordinal inscriptions)
- Bitcoin ordinal endpoints (`/r/blockinfo`)

### ❌ **FORBIDDEN**
- External CDN imports
- HTTP requests to external APIs
- Node.js specific modules
- File system access
- WebAssembly modules

## 🔧 **Troubleshooting**

### Common Issues

1. **Peer dependency warnings**: Use `npm install --legacy-peer-deps`
2. **Import errors**: Verify library exists in import map
3. **Build failures**: Check no external URLs in code
4. **Runtime errors**: Test `/content/` URLs on ordinals.com

### Build Validation
Always test your build:
```bash
npm run build
# Test the build/index.html file locally
```

## 🌟 **Live Example**

**Test inscription**: https://ordinals.com/inscription/33633842

![Example Screenshot](https://github.com/user-attachments/assets/aab7f744-3764-42e5-81bb-e092bc5474ee)

---

## 🤖 **AI Assistant Starter Prompt**

When working with AI assistants on this project, use this prompt to explain the setup:

```
I'm working with a Bitcoin Ordinal inscription development template that uses a dual-mode architecture:

DEVELOPMENT: Uses Node.js modules + Vite dev server with proxy for /content/ requests
PRODUCTION: Builds to single HTML file with dependencies loaded from Bitcoin inscriptions

KEY CONSTRAINTS:
- Only use libraries available in the import map (49 available libraries)
- No external APIs/CDNs allowed in production 
- Must import from package.json "inscriptions" section
- Final output is self-contained HTML file for Bitcoin inscription

AVAILABLE LIBRARIES:
- React Three Fiber ecosystem (@react-three/fiber, @react-three/drei, etc.)
- Three.js + utilities (three, BufferGeometryUtils, etc.) 
- Shader composition (shader-composer suite)
- Animation (@react-spring, @use-gesture)
- Bitcoin-specific (recursive-endpoints, bitmapOCI, bitmon)
- Custom 3D components (GridFloor, boxelGeometry, ecs)

WORKFLOW:
1. npm install --legacy-peer-deps
2. npm run dev (development with proxied ordinals)
3. npm run build (creates inscription-ready HTML)
4. Upload build/index.html to Bitcoin

The project enables modern React Three Fiber development while ensuring Bitcoin inscription compatibility. All dependencies resolve to /content/ URLs in production, making the app fully decentralized.
```

## 📄 **License**

MIT License - Build amazing Bitcoin-native applications!

## 🙏 **Credits**

- **Ordinals Protocol**: https://github.com/ordinals/ord
- **React Three Fiber**: https://github.com/pmndrs/react-three-fiber  
- **Composer Suite**: https://github.com/hmans/composer-suite
- **Vite**: https://vitejs.dev
