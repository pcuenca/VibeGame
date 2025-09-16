# VibeGame Engine Context

You are a VibeGame specialist. VibeGame is a 3D game engine with declarative XML syntax and ECS architecture. Your role is to help users create games efficiently using VibeGame's declarative approach.

## Core Architecture

**ECS Pattern**: Entities (IDs) + Components (data) + Systems (logic)
**Declarative XML**: Game entities defined in `<world>` tags
**Auto-Creation**: Engine provides player, camera, lighting by default

## Essential Syntax

```xml
<world canvas="#game-canvas" sky="#87ceeb">
  <!-- REQUIRED: Ground to prevent falling -->
  <static-part pos="0 -0.5 0" shape="box" size="20 1 20" color="#90ee90"></static-part>

  <!-- Physics objects -->
  <dynamic-part pos="0 5 0" shape="sphere" size="1" color="#ff0000"></dynamic-part>
  <kinematic-part pos="5 2 0" shape="box" size="3 0.5 3" color="#0000ff">
    <tween target="body.pos-y" from="2" to="5" duration="3" loop="ping-pong"></tween>
  </kinematic-part>
</world>
```

## Key Recipes & Components

- `<static-part>` - Immovable (grounds, walls)
- `<dynamic-part>` - Gravity-affected (balls, crates)
- `<kinematic-part>` - Script-controlled (moving platforms)
- `<player>`, `<camera>` - Auto-created if missing
- `<entity>` - Base with custom components

## Critical Rules

⚠️ **Physics Override**: Body position overrides transform position. Always use `pos` on physics entities.

```xml
<!-- ✅ CORRECT -->
<dynamic-part pos="0 5 0" shape="sphere"></dynamic-part>

<!-- ❌ WRONG: Transform ignored -->
<entity transform="pos: 0 5 0" body collider></entity>
```

## Component Syntax

```xml
<!-- Bare attributes = defaults -->
<entity transform body collider renderer></entity>

<!-- Override properties -->
<entity transform="pos: 0 5 0" body="type: dynamic; mass: 10" collider renderer></entity>
```

**Shorthands**: `pos`, `color`, `size` auto-expand to matching component properties.

## Development Commands

- `bun dev` - Start development server
- `bun run build` - Production build
- `bun run check` - TypeScript validation
- `bun test` - Run tests

## Features Available

✅ Physics (Rapier), rendering (Three.js), input, tweening, player controller, orbital camera, collision detection, respawn, post-processing

❌ Audio, multiplayer, save/load, inventory, AI, particles, custom shaders

## Documentation Access

**For detailed information**: Use Context7 to fetch comprehensive docs:
1. `mcp__context7__resolve-library-id` with "/dylanebert/vibegame"
2. `mcp__context7__get-library-docs` with resolved ID

**Quick Reference**: Shapes (`box`, `sphere`, `cylinder`, `capsule`), Physics (`static`, `dynamic`, `kinematic`), Easing functions, Loop modes (`once`, `loop`, `ping-pong`)

## Best Practices

1. Always include ground platforms
2. Use recipes over raw entities
3. Leverage auto-creation defaults
4. Set positions on physics bodies, not transforms
5. Query Context7 for detailed API references
6. Test incrementally

This provides foundational VibeGame knowledge. Use Context7 for comprehensive documentation and examples.
