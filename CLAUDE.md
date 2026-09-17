# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands
The project is a static web application. No build or installation steps are required.
- **Run the game**: Open `index.html` in any modern web browser.

## Code Architecture
The game is implemented as a single-page application using HTML5 Canvas and vanilla JavaScript.

### Structure
- `index.html`: Contains the game's UI structure, including different "screens" (Main Menu, Settings, Tutorial, and the Game Screen).
- `assets/css/game.css`: Defines the visual styling and animations for the UI and game elements.
- `assets/js/game.js`: The core game engine.
    - `CONFIG`: Global constants for physics (gravity, friction, speed, jump force).
    - `SettingsManager`: Manages user preferences (audio volumes/toggles) via `localStorage`.
    - `AudioManager`: Handles sound effects and music (currently implemented as a stub).
    - `LEVELS`: A data-driven array containing all level definitions, including platforms, hazards (lava/water), triggers (pressure plates/gates), and exit points.
    - `Game`: The main controller. It manages the game loop (`requestAnimationFrame`), state transitions (MENU $\rightarrow$ TUTORIAL $\rightarrow$ PLAYING), and level progression.
    - `Player`: Handles movement physics, collision detection with platforms, and interaction with hazards based on the player's element (Fire or Water).
    - `Particle`: Manages simple visual effects for elements and transformations.

### Key Game Mechanics
- **Elemental Interaction**: Fire players die in water; Water players die in lava/fire.
- **Fusion**: In 2-player mode, players can "fuse" by staying close to each other, granting temporary immunity to hazards.
- **Level Triggers**: Some levels require players to activate pressure plates to open gates.
- **Modes**: Supports both 1-player (where the player can switch elements using the `Tab` key) and 2-player cooperative play.
