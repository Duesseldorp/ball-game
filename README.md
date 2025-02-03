# Interactive Ball Game

This browser‑based game challenges you to score points by getting the red ball(s) to fall into a designated “hole”. The game features realistic physics for ball movement and collisions, dynamic size reduction after each round, and a two‑ball mode that activates after a set period.

## Game Overview

- **Gameplay Mechanics:**  
  - A red ball is launched in a container where gravity, damping, and collision physics affect its motion.  
  - When the ball falls completely into the hole, the player scores a point.
  - After a successful score, the game “resets” for a new round with both the ball and the hole reduced in size by 2%.
  - The hole is always maintained at exactly 5% larger than the ball so that the ball can still fit inside it.

- **Two‑Ball Mode:**  
  - After a specified time threshold (currently set to 60 seconds for testing), the game switches to two‑ball mode.
  - In two‑ball mode, two balls are emitted in each round.
  - The round is only completed when **both** balls have fallen into the hole.
  - The game uses improved collision physics so that when the balls touch each other, they bounce off in a realistic, elastic manner.

## Technical Details

- **Client-Side Physics:**  
  - The game simulates gravity (set at 1000 px/s²) and applies a damping factor to simulate friction or air resistance.
  - The ball’s movement, collision with container borders, and ball‑to‑ball collisions are all calculated in JavaScript.
  - Elastic collision formulas are used for realistic interactions between balls in two‑ball mode.

- **Dynamic Sizing:**  
  - Each round, the ball and hole shrink by 2%.  
  - The hole’s size is dynamically recalculated to always be 5% larger than the current ball size.

- **User Interaction:**  
  - Players can interact with the ball using pointer events. When the player clicks (or touches) the ball and drags, an impulse is applied, altering its velocity.
  - Device orientation support is included, allowing the effective gravitational direction to be adjusted based on the device’s tilt.

## Implementation

- **HTML Structure:**  
  - The main HTML file contains a container for the game, a background “404” text for style, and a fixed counter and footer.
  - The interactive elements (ball(s) and hole) are dynamically created and managed via JavaScript.

- **JavaScript Logic:**  
  - The animation loop uses `requestAnimationFrame` for smooth motion updates.
  - Physics calculations (including gravity, damping, collision detection, and collision resolution) are performed on each frame.
  - The game monitors when a ball falls into the hole and updates the score accordingly.
  - In two‑ball mode, a separate collision handling function processes ball‑to‑ball interactions.

## Limitations

- **Client‑Side Only:**  
  - Currently, the game is implemented entirely on the client side using HTML, CSS, and JavaScript.  
  - There is no server‑side score management implemented.  
  - As a result, all game logic is exposed in the browser’s source code.

## Future Improvements

- **Server‑Side Integration:**  
  While not implemented at this stage, a future version might include server‑side score management to prevent client‑side manipulation.
  
- **Enhanced Security:**  
  Additional measures such as code obfuscation and more robust validation could be added to further protect the game logic.
