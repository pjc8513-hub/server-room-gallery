# The Gallery of Forking Paths

An infinite, procedurally generated surrealist art gallery inspired by Jorge Luis Borges' "The Garden of Forking Paths" and Salvador Dalí's "The Persistence of Memory." Walk through an endless corridor lined with dreamlike paintings featuring melting clocks, drooping tables, impossible shadows, and floating eyes—each painting deterministically generated from a seeded random number generator, ensuring the same location always reveals the same surrealist vision.

## 🎨 Live Demo

**[Play the Gallery →](https://YOUR-USERNAME.github.io/server-room-gallery)**

*(Replace `YOUR-USERNAME` with your GitHub username and enable GitHub Pages in your repository settings.)*

## 🎮 Controls

| Input | Action |
|-------|--------|
| **W / ↑** | Move forward |
| **S / ↓** | Move backward |
| **A / ←** | Strafe left |
| **D / →** | Strafe right |
| **Mouse Move** | Look around (click canvas first to lock pointer) |
| **Click Canvas** | Lock/unlock pointer |
| **Touch (Mobile)** | Swipe to look around |

## 🏛️ Gallery Features

- **Infinite Corridor**: A 6×4 unit hallway stretching 200 units deep with classical molding and dark wood runner
- **64 Paintings**: Procedurally generated surrealist canvases with deterministic seeded RNG (the visible set is offset by a random index each load)
- **Random Start & Warp**: When the page opens you may begin in a different mathematical region; press **`R`** to jump to a new random location (including a new lateral position and view direction) and regenerate the artwork
- **Painting Elements**:
  - Atmospheric sky gradients (twilight, void, bruised purple, arctic gold)
  - Melting clocks with drooping drips (à la Dalí)
  - Floating tables with drooping legs
  - Solitary figures and pale obelisks
  - Floating eyes with colored irises
  - Wrong-direction shadows (physically impossible)
  - Ground reflections
  - Terrain with erosion cracks
- **Dynamic Titles**: Each painting receives a algorithmically-generated title from word lists
- **Golden Frames**: Alternating dark and bright gold frames
- **Gallery Lighting**: Ambient light + individual spotlights over each painting
- **First-Person Navigation**: Walk freely with pointer lock support
- **Responsive Design**: Works on desktop and mobile browsers

## 🛠️ Technical Notes

### No Build Tools Required
This is a **zero-dependency static site**:
- Pure **vanilla HTML/CSS/JavaScript**
- **Three.js r128** loaded via CDN
- **No npm, webpack, vite, or bundlers**
- Works offline after initial load

### Procedural Painting Generation
Each painting is generated on a 64×64 Canvas element using:
- **Mulberry32**: Seeded pseudorandom number generator
- **Deterministic rendering**: Same index = same painting every time
- **Composite layers**: Sky, terrain, objects, shadows, reflections
- **Texture wrapping**: Canvas converted to Three.js textures

### Scene Architecture
- **WebGL Renderer**: Full-window canvas with black background
- **Fog**: Exponential fog (density 0.045) for depth perception
- **Lighting**:
  - Ambient light: #1a0f08, intensity 1.2
  - Per-painting spotlights: warm white #ffe8a0, intensity 1.2
- **Camera**: Eye-height perspective (y = 1.7), 75° FOV
- **Collision**: Constrained movement within corridor bounds

## 📁 File Structure

```
server-room-gallery/
├── index.html              ← Single self-contained application
├── README.md               ← This file
└── .github/
    └── workflows/
        └── deploy.yml      ← GitHub Actions auto-deploy
```

## 🚀 Deployment

### 1. Create GitHub Repository

```bash
# Create a new repo on GitHub called 'server-room-gallery'
# (or any name you prefer)

# Initialize and push your local code
git init
git add .
git commit -m "Initial Three.js gallery"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/server-room-gallery.git
git push -u origin main
```

### 2. Configure GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under "Build and deployment":
   - **Source**: Select "Deploy from a branch"
   - **Branch**: Select `gh-pages` (will be created by the workflow)
   - **Folder**: Select `/ (root)`
4. Save

### 3. The Workflow Handles Deployment

The `.github/workflows/deploy.yml` file automatically:
- Triggers on every push to `main`
- Checks out your code
- Pushes the repo root to the `gh-pages` branch
- GitHub Pages serves the `gh-pages` branch

**No manual deployment steps needed!**

### Expected Live URL

Once deployed, your gallery will be live at:

```
https://YOUR-USERNAME.github.io/server-room-gallery/
```

(Or your custom domain if configured.)

## 🎭 Inspiration

- **"The Garden of Forking Paths"** by Jorge Luis Borges — infinite branching narratives and procedural generation
- **"The Persistence of Memory"** by Salvador Dalí — melting clocks, impossible physics, dreamlike landscapes
- **Generative art** — deterministic randomness and layered complexity

## 📜 License

MIT License. See LICENSE file for details. Feel free to fork, modify, and host your own version.

## 🔧 Tips & Customization

- **Adjust corridor size**: Edit `corridorWidth`, `corridorHeight`, `corridorLength`
- **Change painting count**: Modify the loop starting at `for (let z = -corridorLength / 2 + 5;...)`
- **Modify color palettes**: Edit `skyPalettes` and color constants in the painting generator
- **Adjust lighting**: Tweak `AmbientLight` intensity and `SpotLight` parameters
- **Change movement speed**: Set `controls.speed` (currently 3.5 units/sec)
- **Add new painting layers**: Extend the procedural generator with additional drawing operations

## 🤝 Contributing

Found a bug? Have a creative idea? Feel free to open an issue or PR!

---

**Walk the infinite gallery. Every visit is the same painting, yet every painting is unique.**
