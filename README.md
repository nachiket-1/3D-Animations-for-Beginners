<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20,15,10,5,30&height=220&section=header&text=🌀%203D%20Animations&fontSize=52&fontColor=ffffff&animation=fadeIn&fontAlignY=38&desc=Python%20Animations%20for%20Beginners%20—%20Part%202&descAlignY=58&descSize=19" width="100%"/>

<br/>

[![Python](https://img.shields.io/badge/Python-3.8%2B-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
[![Matplotlib](https://img.shields.io/badge/Matplotlib-3D-11557C?style=for-the-badge&logo=python&logoColor=white)](https://matplotlib.org/stable/gallery/mpl_toolkits/)
[![NumPy](https://img.shields.io/badge/NumPy-1.21%2B-013243?style=for-the-badge&logo=numpy&logoColor=white)](https://numpy.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=for-the-badge&logo=jupyter&logoColor=white)](https://jupyter.org)
[![Kaggle](https://img.shields.io/badge/View%20Animations%20on-Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)
[![License](https://img.shields.io/badge/License-MIT-7f5af0?style=for-the-badge)](LICENSE)

<br/>

> *"The third dimension is where flat data becomes a living world."*

<br/>

**Go one dimension deeper. Rotate. Spiral. Orbit.** 🚀

<br/>

</div>

---

> ⚠️ **GitHub cannot render animations inside `.ipynb` files.**
> All 4 animations are fully interactive and viewable on the Kaggle page:
>
> **👉 [View all animations live on Kaggle](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)**

---

## 📖 About

This is **Part 2** of the Python Animations for Beginners series. While Part 1 covered the fundamentals of 2D animation with `FuncAnimation`, Part 2 takes everything you learned and adds a **Z axis**.

Using `mpl_toolkits.mplot3d` — a toolkit bundled inside Matplotlib — you'll build four 3D animations from scratch, understand how camera control works, and learn the specific patterns that make 3D animation different from 2D.

No prior 3D experience needed. If you've done Part 1, you're ready.

> **Note:** GitHub renders `.ipynb` files as static code — animations won't play. To see all 4 animations running live, visit the **[Kaggle notebook](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)**.

---

## 🗺️ Table of Contents

- [View Animations Live](#-view-animations-live)
- [What's Inside](#-whats-inside)
- [Animations Preview](#-animations-preview)
- [2D vs 3D — Key Differences](#-2d-vs-3d--key-differences)
- [Quick Start](#-quick-start)
- [Requirements](#-requirements)
- [Run on Kaggle](#-run-on-kaggle)
- [Run Locally](#-run-locally)
- [3D Cheat Sheet](#-3d-cheat-sheet)
- [Experiment Ideas](#-experiment-ideas)
- [The Full Series](#-the-full-series)

---


## 🎥 View Animations Live

GitHub displays `.ipynb` notebooks as static text — the animations are code, not videos, so they won't play here.

**To see all animations running:**

[![View on Kaggle](https://img.shields.io/badge/▶%20Watch%20All%204%20Animations-Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)

> Open the Kaggle notebook → click **Run All** → every animation renders as an interactive player directly in the output. You can pause, scrub, and replay each one.

---

## 📦 What's Inside

| # | Animation | New Concepts | Difficulty |
|---|-----------|-------------|------------|
| 1 | **Rotating 3D Scatter Cloud** | `projection='3d'`, `ax.view_init()`, camera rotation | 🟢 Easy |
| 2 | **Rippling 3D Surface Wave** | `meshgrid`, `plot_surface`, remove & redraw pattern | 🟡 Medium |
| 3 | **Growing Double Helix** | Parametric 3D curves, `set_3d_properties()`, DNA rungs | 🟡 Medium |
| 4 | **Planet + Orbiting Moon** | Multiple 3D objects, trails, surface positioning | 🟠 Intermediate |

Plus a full **3D Cheat Sheet** and **"What's Next"** challenge list at the end.

---

## 🎬 Animations Preview

```
🔵  Rotating Scatter     · · ·           200 colored points
                      ·    ·  ·          rotating 360°
                         · ·             colored by height

🌊  Surface Wave       ╭─╮╭─╮            rippling 3D mesh
                      ╯  ╰╯  ╰           travelling outward
                     ╭──────────╮        + slow rotation

🧬  Double Helix           /              two strands growing
                       ───/               upward together
                      /  ╲               with DNA rungs

🪐  Planet + Moon      ●                 sphere planet
                    ○ ─ ─ ─              moon orbiting
                      · · ·              with glowing trail
```

---

## ⚡ 2D vs 3D — Key Differences

Everything from Part 1 still applies. Here's what changes in 3D:

```python
# ── PART 1 (2D) ──────────────────────────────
fig, ax = plt.subplots()               # 2D axes
line.set_data(x, y)                    # update x and y
ani = FuncAnimation(..., blit=True)    # blit works fine

# ── PART 2 (3D) ──────────────────────────────
fig = plt.figure()
ax  = fig.add_subplot(projection='3d') # 3D axes ← only change!
line.set_data(x, y)
line.set_3d_properties(z)              # also update z ← new!
ani = FuncAnimation(..., blit=False)   # 3D doesn't support blit
```

**The camera rotation trick — the heart of 3D animation:**

```python
def update(frame):
    ax.view_init(elev=20, azim=frame * 2)  # rotate 2° per frame
    # That's it. The scene rotates automatically!
```

| Parameter | What it controls |
|-----------|-----------------|
| `elev` | How high up you're looking from (0° = side, 90° = top-down) |
| `azim` | Horizontal rotation around the scene (0°–360°) |

---

## ⚡ Quick Start

### Option 1 — Kaggle (Recommended, Zero Setup)

[![Open in Kaggle](https://kaggle.com/static/images/open-in-kaggle.svg)](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)

The notebook is already live on Kaggle — just open and run:

**👉 [kaggle.com/code/nachikettalekar/3d-animations-for-beginners](https://www.kaggle.com/code/nachikettalekar/3d-animations-for-beginners)**

1. Click the link above
2. Hit **Copy & Edit** to run it in your own Kaggle session
3. Click **Run All** ▶️ — all 4 animations render right in the output

All libraries are pre-installed on Kaggle — no setup needed!

### Option 2 — Google Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com)

1. Go to [colab.research.google.com](https://colab.research.google.com)
2. **File → Upload notebook** → select the `.ipynb` file
3. Hit **Runtime → Run All**

### Option 3 — Run Locally

```bash
git clone https://github.com/nachiket-1/python-animations-3d.git
cd python-animations-3d
pip install -r requirements.txt
jupyter notebook python_animations_part2.ipynb
```

---

## 📋 Requirements

```txt
matplotlib>=3.5.0
numpy>=1.21.0
ipython>=7.0.0
```

`mpl_toolkits.mplot3d` is **bundled inside Matplotlib** — no separate install needed!

```bash
pip install -r requirements.txt
```

> ✅ All dependencies are pre-installed on Kaggle and Google Colab.

---

## 🏁 Run on Kaggle

1. Upload the notebook via **File → Import Notebook**
2. Run all cells — no additional installs required
3. Each animation renders as an interactive HTML player inside the notebook

> **Heads up:** 3D animations are slightly slower to render than 2D since `blit=False` redraws the full frame every time. This is normal — the output is worth the wait!

---

## 💻 Run Locally

```bash
# 1. Clone the repo
git clone https://github.com/nachiket-1/python-animations-3d.git
cd python-animations-3d

# 2. (Recommended) Virtual environment
python -m venv venv
source venv/bin/activate      # macOS / Linux
venv\Scripts\activate         # Windows

# 3. Install
pip install -r requirements.txt

# 4. Launch
jupyter notebook
```

---

## 📋 3D Cheat Sheet

```python
# Create 3D axes
fig = plt.figure()
ax  = fig.add_subplot(projection='3d')

# Rotate camera (the core 3D animation trick)
ax.view_init(elev=20, azim=frame * 2)

# 3D scatter
ax.scatter(x, y, z, c=colors, s=20)

# 3D line — set_data + set_3d_properties
line, = ax.plot([], [], [])
line.set_data(x, y)
line.set_3d_properties(z)

# 3D surface
X, Y = np.meshgrid(x, y)
Z = np.sin(X) * np.cos(Y)
surf = ax.plot_surface(X, Y, Z, cmap='plasma')

# Animate a surface — remove and redraw
surf = [ax.plot_surface(X, Y, Z, cmap='plasma')]
def update(frame):
    surf[0].remove()
    surf[0] = ax.plot_surface(X, Y, new_Z, cmap='plasma')

# Clean dark look
ax.set_axis_off()
ax.xaxis.pane.fill = False

# ALWAYS use blit=False for 3D
ani = FuncAnimation(fig, update, frames=120, blit=False)
```

---

## 🧪 Experiment Ideas

After going through the notebook, try these challenges:

- 🦋 **Lorenz Attractor** — one of the most beautiful chaotic systems in math. Three equations, infinite complexity
- 🍩 **Torus (Donut)** — parameterize with two angles `(u, v)` and animate rotation
- 🌍 **Textured Sphere** — map an image onto a sphere using `ax.plot_surface`
- 🎆 **3D Fireworks** — particles exploding outward from a point with gravity
- 📊 **3D Bar Chart** — use `ax.bar3d()` with animated growing heights
- 🌀 **Möbius Strip** — a one-sided surface that looks impossible

---

## 📚 The Full Series

| Part | Topic | Link |
|------|-------|------|
| **Part 1** | 2D Animations — Moving dots, sine waves, bouncing ball, solar system | [View Notebook](https://github.com/YOUR_USERNAME/python-animations) |
| **Part 2** | 3D Animations — Scatter clouds, surfaces, helix, orbiting moon | You are here ✨ |

---

## 🤝 Contributing

Have a cool 3D animation idea to add?

1. Fork the repository
2. Create a branch: `git checkout -b feature/lorenz-attractor`
3. Add your animation with beginner-friendly comments
4. Submit a Pull Request

---

## 📄 License

This project is open source under the **MIT License**.

---

<div align="center">

**Made with ❤️, Python, and the Z axis**

If this helped you go 3D, drop a ⭐ on the repo!

<img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=20,15,10,5,30&height=120&section=footer" width="100%"/>

</div>
