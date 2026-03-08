# Jezzball-style Partition Game Implementation Plan

The goal is to build a web-based game where the player partitions a square area to trap bouncing obstacles, similar to the classic games Jezzball or Qix.

## Proposed Changes

We will build this using Vanilla JavaScript, HTML5 Canvas, and modern CSS.

### Game Application
*   **[NEW] `index.html`**: The main entry point, containing the game canvas, score UI, and a welcome screen.
*   **[NEW] `style.css`**: CSS styling for a modern, sleek arcade look (dark mode, neon colors, glassmorphism UI elements).
*   **[NEW] `main.js`**:
    *   **Game Loop**: `requestAnimationFrame` based loop.
    *   **State Management**: Handling game states (Start, Playing, GameOver, LevelComplete).
    *   **Entities**:
        *   `Ball`: Objects moving and bouncing inside the game area.
        *   `Wall`: Static boundaries and filled areas.
        *   `Builder`: The lines drawn by the player to create new walls.
    *   **Logic**:
        *   Collision detection between balls, walls, and builders.
        *   Area calculation to determine when a partitioned area is empty and should be filled.
        *   Input handling for mouse/touch to initiate vertical or horizontal wall building.

## Approach details
The game area will be represented as a grid or a set of rectangles. When a player clicks/drags, a "builder" line expands in both directions until it hits an existing wall or edge. If a ball hits a growing builder line, the player loses a life. If the builder line reaches walls on both sides, it becomes a permanent wall, and any enclosed area containing no balls is "filled" and awarded as points.

## Verification Plan

### Automated Tests
Not applicable for this highly visual canvas game.

### Manual Verification
1.  Open `index.html` in a web browser.
2.  Verify the balls are moving randomly and bouncing off the edges.
3.  Click/drag to partition the area.
4.  Verify that if a ball touches a growing line, a life is lost.
5.  Verify that if an area is completely partitioned off without balls, it gets filled.
6.  Verify that the game tracks the percentage of the area filled and progresses to the next level/ends the game appropriately.
