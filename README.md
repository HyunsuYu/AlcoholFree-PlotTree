# AlcoholFree-PlotTree

A node-graph–based visual novel authoring tool (**PlotTree**) and the earlier version of the visual novel **ALCOHOL FREE** authored with it.

> This repository is reference **[2]** of the paper *"A Visual-Novel Authoring Framework with a Frame-State Execution Model Inspired by Render State Tables (Visual Wave)"* — the **predecessor node-graph authoring tool** that Visual Wave improves upon.
>
> 📄 **Paper:** https://hyunsuyu.github.io/assets/papers/VisualWavePaper.pdf

## Overview

- **Engine:** Unity 2022.3 (C#)
- The repository holds two things together:
  1. **PlotTree authoring tool** — a node-graph editor that represents each Scene as a node and scene-to-scene transitions as edges (similar to Unreal Blueprint / Unity Shader Graph), together with a **PowerPoint-style slide UI** for editing the frames within each scene.
  2. **ALCOHOL FREE (earlier version)** — the visual novel authored with that tool.

## Authoring model — the baseline compared in the paper

PlotTree stores each screen (frame) as an object holding the **entire state** — background, characters, audio, and effects. Because the full state is rewritten on every frame even when nothing changes, the scene data (`Assets/StreamingAssets/PlotData.json`) is a sequence of per-frame full-state snapshots. This "rewrite the whole state every frame" approach is exactly what Visual Wave replaces with a **declare-only-the-delta frame-state model**, and the paper's quantitative comparison (bytes per dialogue character, state-redundancy ratio, and so on) is measured against this data.

## Structure

```
Assets/
├─ Scripts/                 PlotTree authoring tool + game logic
│  └─ UIs/PlotTreePage/     node-graph editing (Link, SceneItem, ScreenTransition, GlobalVariableCondition, …)
├─ StreamingAssets/
│  └─ PlotData.json         scene graph + per-frame (full-state) data
├─ Scenes/  Prefabs/  Materials/  Shaders/  Fonts/  …
```

## Not included (important)

The following are excluded from this public repository to respect redistribution limits. Restoring them is required to build or run the project as-is.

- **Febucci Text Animator** (`Assets/Plugins/Febucci`) — a paid Unity Asset Store asset that may not be redistributed. Install it from the Asset Store to build.
- **Game art** (`Assets/Resources`) — characters, backgrounds, CGs, and other team-created assets, excluded from the public repository.

This repository is therefore a **reference for the tool's design and data format**, not a complete, runnable build of the game.

## Author & use

- Hyun-su Yu (유현수), Dept. of Computer Engineering, Tongmyong University
- The narrative and assets of *ALCOHOL FREE* are copyright of the development team. The code and data are published for research reference.
