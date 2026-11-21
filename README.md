# MicroFlow 3D: can light see inside your arm?

Interactive 3D model of a real human forearm (skin, 22 muscles, radius and ulna) showing how a low-cost
patch of near-infrared LEDs and detectors located a hidden absorbing target 14 mm under the skin to within
2.4 mm, in a Monte Carlo light-transport simulation.

**Live demo:** open `index.html` in a browser, or deploy this folder as a static site (Vercel, GitHub Pages, Netlify).

## How the result was produced
- **Anatomy:** right forearm surfaces from BodyParts3D, converted to a 0.5 mm voxel model (skin, subcutaneous fat, muscle, bone).
- **Probe:** 4 x 4 near-infrared sources and 4 x 4 detectors, 10 mm apart, on the palm-side skin.
- **Light transport:** MCX Monte Carlo, 30 million photons per optode, on a laptop GPU (RTX 4060).
- **Reconstruction:** Rytov sensitivity matrix, Tikhonov regularization with depth compensation; 224 usable source-detector pairs.
- **Result:** reconstructed peak 2.4 mm from the true target centre, 70% of its contrast recovered.

This is a simulation study, not a medical device.

## Credits
- Anatomy: BodyParts3D, © The Database Center for Life Science (DBCLS), licensed under
  [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). STL conversion by Kevin M. Moerman
  (github.com/Kevin-Mattheus-Moerman/BodyParts3D).
- Light transport: MCX (Monte Carlo eXtreme), Qianqian Fang et al.
- 3D rendering: three.js.

## Deploy on Vercel
1. Push this folder to a GitHub repository.
2. In Vercel: **Add New → Project → Import** the repository.
3. Framework preset: **Other**. Leave build command and output directory empty. Click **Deploy**.
