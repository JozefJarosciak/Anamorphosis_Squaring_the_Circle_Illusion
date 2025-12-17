# Squaring the Circle - Anamorphosis Illusion

An interactive 3D visualization of the famous "Squaring the Circle" anamorphic sculpture, where a single continuous curve appears as a **perfect square** from one viewing angle and a **perfect circle** from 90 degrees away.

![Demo](square-to-circle-effect.mp4)

**Live Demo:** [View on GitHub Pages](https://jozefjarosciak.github.io/Anamorphosis_Squaring_the_Circle_Illusion/)

## The Illusion

This optical illusion demonstrates anamorphosis - a distorted projection that appears normal when viewed from a specific angle. The sculpture exists in 3D space but projects two completely different 2D shapes depending on your viewpoint:

- **Looking down the Y-axis** → Perfect Square
- **Looking down the Z-axis** → Perfect Circle

See the original inspiration: [Video on X/Twitter](https://x.com/PhysInHistory/status/2001025585292959947)

## The Mathematics

The curve is defined as the **intersection of two 3D primitives**:

### 1. Circular Cylinder (along Z-axis)
$$x^2 + y^2 = r^2$$

### 2. Square Prism (along Y-axis)
$$\max(|x|, |z|) = r$$

### The Intersection Curve

Where these two shapes intersect, we get four distinct segments (with r = 1):

| Segment | Description | Parametric Form |
|---------|-------------|-----------------|
| **1. Right Edge** | Vertical line at x=1 | `(1, 0, z)` where z: 1 → -1 |
| **2. Bottom Arc** | Semicircle at z=-1 | `(cos(θ), sin(θ), -1)` where θ: 0 → π |
| **3. Left Edge** | Vertical line at x=-1 | `(-1, 0, z)` where z: -1 → 1 |
| **4. Top Arc** | Semicircle at z=1 | `(cos(θ), sin(θ), 1)` where θ: π → 2π |

### Why It Works

**Square View (Y-axis projection):**
- The two vertical edges project as the left and right sides of the square
- The two semicircular arcs project as the top and bottom sides (circles viewed edge-on appear as lines)

**Circle View (Z-axis projection):**
- The two semicircular arcs project as two halves of a circle
- The two vertical edges project as single points at the left and right (lines viewed end-on appear as points)

### Orthographic Projection

The illusion works best with **orthographic camera projection** (parallel projection), which preserves the true shapes without perspective distortion. This is why the visualization uses an orthographic camera by default.

## Features

- **Interactive 3D View** - Drag to rotate, scroll to zoom
- **Preset Views** - Quick buttons for Square View, Circle View, and Reset
- **Dark/Light Themes** - Toggle between color schemes
- **Sparkler Effect** - Animated particle system with burning coal core
- **Real-time Camera Data** - Editable azimuth, elevation, distance, and position values
- **Orthographic Camera** - Perfect geometric projection for the illusion

## Controls

| Action | Control |
|--------|---------|
| Rotate view | Click and drag |
| Zoom | Scroll wheel |
| Square view | Click "Square View (Y-axis)" button |
| Circle view | Click "Circle View (Z-axis)" button |
| Reset view | Click "Reset View" button |
| Change theme | Use Theme dropdown |
| Toggle sparkle effect | Use Style dropdown |
| Manual camera control | Edit values in Camera Data panel |

## Technical Implementation

Built with:
- **Three.js** - 3D rendering
- **WebGL Shaders** - Custom GLSL shaders for sparkler particles and burning coal effect
- **Pure HTML/CSS/JS** - Single file, no build process required

### Sparkler Effect

The sparkler visualization includes:
- **5000 particles** spawning along the curve
- **Physics simulation** with gravity and air resistance
- **Lifetime-based color gradient** (white → yellow → orange → red in dark mode)
- **Custom spark shape shader** with bright core and radiating rays
- **Animated burning coal material** using fractal Brownian motion noise

## File Structure

```
Anamorphosis_Squaring_the_Circle_Illusion/
├── index.html          # Complete application (single file)
├── README.md           # This file
└── square-to-circle-effect.mp4  # Demo video
```

## Running Locally

Simply open `index.html` in a modern web browser. No server or build process required.

```bash
# Or use a local server for best results:
npx serve .
# Then open http://localhost:3000
```

## References

- [Original Video Inspiration](https://x.com/PhysInHistory/status/2001025585292959947)
- [Anamorphosis - Wikipedia](https://en.wikipedia.org/wiki/Anamorphosis)
- [Three.js Documentation](https://threejs.org/docs/)

## License

MIT License - Feel free to use, modify, and share.

---

*Created with Three.js and WebGL*
