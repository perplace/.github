# Perplace

**Worlds that agents can inhabit.** Editable cities, buildings and interiors from real map data, delivered as structured data first and pixels second.

Perplace turns an area on the map into a complete world: streets, blocks, buildings with facades and roofs, floors, rooms and furnished interiors. Every part of it has a stable id, typed fields and a meaning an agent can query, so the same world runs in a game engine, a simulator or an AI evaluation loop without hand-placed waypoints.

- Product: https://www.perplace.com
- Data model: https://www.perplace.com/docs/
- Work log: https://www.perplace.com/changelog/
- Early access: https://www.perplace.com/#early-access · hello@perplace.com

## What a world contains

One tree, four scales. A city holds buildings, a building holds floors, a floor holds rooms, and a room holds objects. Interiors are a flat list of convex primitives in metres, Y up, each naming its material, its group and its room:

```json
{
  "id": "p339",
  "shape": "rounded",
  "pos": [6.4, 0.3, 5.8],
  "size": [4.6, 0.35, 1.1],
  "material": "walnut",
  "group": "objects",
  "room": "living"
}
```

Objects group primitives and give them meaning: bilingual names, uses (sit, lie down, open, look out, pick up), access points for an agent, articulation with named states, mobility and mass, collision pieces, surfaces and storage. A door's hinge sits on the real jamb and keeps the state the last action left it in:

```json
{
  "kind": "hinge",
  "parts": ["p273"],
  "axis": [0, 1, 0],
  "pivot": [0.36, 1.2, 3.41],
  "rangeRad": [0, 1.45],
  "states": { "closed": { "value": 0 }, "ajar": { "value": 0.22 }, "open": { "value": 1.45 } },
  "current": "open"
}
```

## Delivery

The same world ships in the representation your project needs: JSON (the structured world), USD (one transform per object with the Perplace attributes, rooms with bounds, provenance hash), glTF / GLB (the visual scene) and simulation grids (walkable and blocked cells at the resolution you request). Blender, Unreal Engine, Unity, Godot, Houdini, Omniverse and three.js read at least one of them. Materials are named, not baked; collision is convex as is; no physics is baked.

## Status

Private beta with paid pilots. Source stays private; this organization hosts what we publish for integrators as it becomes stable. To join the beta or ask about a city, write to hello@perplace.com.
