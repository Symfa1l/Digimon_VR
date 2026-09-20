# Digimon Digital World VR

An interactive **WebXR** scene built with **A-Frame** where you step into the "Digital World", raise Digimon through their evolution lines, and trigger a Jogress fusion into Omegamon.

> **Solo project** – a course project and non-commercial fan tribute.
> *Digimon and all related characters, music and footage belong to their respective owners (Bandai, Toei Animation, and others). This repository is for education and portfolio purposes only.*

**▶ Live demo:** TODO: add GitHub Pages link
**Tested on:** TODO: e.g. Chrome on Windows / Meta Quest Browser

<!-- TODO: add screenshots or a short GIF: e.g. ![Evolution stations](docs/stations.png) -->

## What you can do

1. **Initialize the dive** – the start button unlocks once all assets have loaded. A typewriter terminal ("LINKING TO DIGITAL WORLD…"), a gate sound effect, a wormhole tunnel and a fade take you into the lab.
2. **Use the 3 evolution stations** – click a terminal to open its menu and evolve step by step (you can only advance to the next stage):
   - Agumon → Greymon → MetalGreymon → WarGreymon
   - Gabumon → Garurumon → WereGarurumon → MetalGarurumon
   - V-mon → XV-mon → Paildramon → Imperialdramon → Imperialdramon Fighter Mode
3. **Watch the evolution cutscene** – each evolution plays a video on a cinema screen in a separate environment, then the new 3D model appears at the station. You can skip the video or toggle 1×/2× speed.
4. **Unlock Omegamon** – bring the Agumon line and the Gabumon line to their final stage to open the Jogress altar and fuse them into Omegamon (with the option to cancel and split them back).
5. **Control the audio** – play/pause and change the volume of the background music.

**14 3D models** in total.

## Controls

| Action | Input |
|---|---|
| Look around | Mouse drag |
| Move | `W` `A` `S` `D` |
| Interact | Click terminals and buttons |
| VR | "Enter VR" button (A-Frame) on a WebXR-capable browser/headset |

## Technical notes

Custom A-Frame components written for this project:

| Component | Purpose |
|---|---|
| `auto-fit` | After a model loads, measures its bounding box (`THREE.Box3`) and scales/centers it to fit a station regardless of the original model size |
| `lab-boundary` | Keeps the player inside a circular lab area each frame |
| `evolution-station` | Menu logic, stage unlocking, cutscene playback, model swapping, and saving/restoring the player's position and view direction |
| `omegamon-system` | Listens for a `check-jogress` event, checks both stations' stages, and runs the fusion and cancel flow |
| `volume-controller` | Music and cutscene controls (play, pause, volume, skip, speed) |

Other details:

- The cutscene environment is swapped in at a different height while the lab is moved away, so the two scenes never overlap.
- `a-assets` with a timeout preloads models and audio; a loading panel shows the status of each asset.
- Shared state (`digiState`) tracks each station's current stage.

## Run locally

Browsers block media loading from `file://`, so serve the folder:

```bash
python -m http.server 8000
# open http://localhost:8000
```

> The repository is large (about 226 MB because of the videos). For faster loading, compress the videos before deploying to GitHub Pages.

## 3D model credits

All models are from Sketchfab, licensed **CC BY 4.0** unless noted.

| Model | Author | Source |
|---|---|---|
| Agumon | aaandro | https://sketchfab.com/3d-models/agumon-00bafb51a08946ffbc35d49fd1946f17 |
| Greymon (sculpt) | Rude Randal | https://sketchfab.com/3d-models/digimon-greymon-sculpt-b52108461e504bc3b33ab01353823cc8 |
| Metal Greymon (Digimon Linkz) | akennedy007 | https://sketchfab.com/3d-models/digimon-linkz-metal-greymon-d107488764574e2c9744a2dd2a1301ee |
| War Greymon (Digimon Links) | DrewsDigitalDesigns | https://sketchfab.com/3d-models/war-greymon-digimon-links-b20f20503d684edd8df534d6c1a6b628 |
| Gabumon (Digimon Masters) | donmcdonough | https://sketchfab.com/3d-models/digimon-masters-gabumon-2c04be76533b425090fa209832409b6a |
| Garurumon | medothegeek | https://sketchfab.com/3d-models/garurumon-gabumon-line-digimon-5b3a32eb5a1c47a5883fd3db3431b92a |
| WereGarurumon | medothegeek | https://sketchfab.com/3d-models/weregarurumon-gabumon-line-digimon-ad4b2c7ac55244e2b081e298bcf5c811 |
| MetalGarurumon | theamazingdonovan207 | https://sketchfab.com/3d-models/metalgarurumon-robotic-wolf-b09a6e04af9a43069400daffd3e3d4f3 |
| Veemon (Anniversary) | xeratdragons | https://sketchfab.com/3d-models/veemon-digimon-anniversary-a2fef65ef43f4af0a704343e6433ad45 |
| XV-mon | kishi | https://sketchfab.com/3d-models/digimon-xv-mon-1464ade0fed347b4a1aa44250a17718f |
| Paildramon | darkengine | https://sketchfab.com/3d-models/paildramon-dfa02a8323a3499da3bc7d3a21c42ba1 |
| Imperialdramon | kishi | https://sketchfab.com/3d-models/digimon-imperialdramon-1b9ee3aaf3ba40e08c19ee60ba2181e4 |
| Imperialdramon Fighter Mode | pkturtle | https://sketchfab.com/3d-models/imperialdramon-fighter-mode-374d500e17a242d4990e62034593e58e (**CC BY-SA 4.0**) |
| Omegamon X-Antibody | LorisC93 | https://sketchfab.com/3d-models/omegamon-x-antibody-e931f451376e425e9465b3ce5d0af39b |

Framework: [A-Frame](https://aframe.io/) 1.5.0.
Music and video clips: property of their respective copyright holders, used for non-commercial demonstration only.
