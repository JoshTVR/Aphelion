# Aphelion

> *The farthest point from the sun in an orbit. The coldest, darkest moment — before the pull back begins.*

**Aphelion** is a dark atmospheric 3D RPG/Adventure built in Unity 6 with URP. The protagonist starts at their lowest point and has to find the way back. Exploration, melee combat, dialogues, quests, and a narrative told through environment and atmosphere.

This repository also contains the **Aphelion Unity Developer Series** — a complete 55-chapter self-taught programming guide built alongside the game, covering Unity development from zero to professional level.

---

## The Game

| | |
|---|---|
| **Engine** | Unity 6 (URP) |
| **Genre** | RPG / Adventure 3D |
| **Perspective** | Third person |
| **Tone** | Dark, atmospheric, narrative-driven |
| **Inspiration** | The loneliness and transcendence of Bowie's *Space Oddity*, Elton John's *Rocket Man* — a lone figure at the farthest point, and the journey back |

---

## The Documentation Series

55 chapters across 5 volumes. Each chapter follows the same structure: *why* before *how*, guided exercises, and a 3-hint system for independent challenges so there's never a dead end.

### Volume 1 — The Foundation
*Milestone: Character moving in the world, camera, collisions, main menu*
> Unity is not magic — it's a component system you control

Cap 1–12: Editor, GameObjects, MonoBehaviour, variables, methods, input, physics, camera, conditionals, arrays, debugging, scenes.

### Volume 2 — Core Systems
*Milestone: Item pickups, inventory with HUD, animations, audio, save system*
> Systems don't talk directly — they communicate through events

Cap 13–24: OOP, events/delegates, triggers, ScriptableObjects, inventory, UI, animator, audio, save/load, coroutines, object pooling.

### Volume 3 — Gameplay Systems
*Milestone: AI enemies, combat, quests, dialogues, dynamic weather*
> Complex behaviors are State Machines + data

Cap 25–36: State machines, NavMesh (AI Navigation), interfaces, combat (x2), quests, dialogues, weather/day cycle, backtracking (x2), profiling, New Input System.

### Volume 4 — Advanced Architecture
*Milestone: Publishable game with cinematics, shaders, settings menu, build*
> Good code isn't code that works — it's code others can understand and extend

Cap 37–45: SOLID, Service Locator/DI, generics/extensions, procedural generation, Timeline, URP/VFX, minimap, settings menu, build & distribution.

### Volume 5 — Full Independence
*Milestone: Read official docs, write your own tools, work without AI*
> A professional programmer doesn't know everything — they know where to look

Cap 46–55: LINQ, testing, custom editor tools, Cinemachine 3.x, IK, advanced animation, asset management, how to learn, polish/game feel, final integration.

---

## Project Structure

```
Assets/
├── Documentation/
│   ├── Volume1/    (13 files — Cap01–12 + index)
│   ├── Volume2/    (13 files — Cap13–24 + index)
│   ├── Volume3/    (13 files — Cap25–36 + index)
│   ├── Volume4/    (10 files — Cap37–45 + index)
│   └── Volume5/    (11 files — Cap46–55 + index)
├── Scripts/        (written chapter by chapter)
└── Scenes/         (built during the series)
```

---

## Status

| Volume | Chapters | Documentation |
|--------|----------|--------------|
| Volume 1 — The Foundation | 12/12 | Complete |
| Volume 2 — Core Systems | 12/12 | Complete |
| Volume 3 — Gameplay Systems | 12/12 | Complete |
| Volume 4 — Advanced Architecture | 9/9 | Complete |
| Volume 5 — Full Independence | 10/10 | Complete |

Documentation: **55/55 chapters** — audited and updated for Unity 6.

Game: in development, following the series from Vol. 1.

---

## Unity 6 Compatibility

All 55 chapters have been audited for Unity 6 compatibility. Key updates applied:
- **Cinemachine 3.x** — complete rewrite of Cap49 (new API: `CinemachineCamera`, `CinemachineOrbitalFollow`, etc.)
- **AI Navigation package** — Cap26 updated for `NavMeshSurface` workflow
- **Render Graph** — Cap42 extended with Unity 6 custom pass approach
- **UI Toolkit** — Cap18 extended with modern UI alternative

---

*Built as a self-taught learning project. The documentation is the map. The game is the destination.*
