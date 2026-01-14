# 🎓 Learning Guide: Baking Shota (Cat-Sweets)

This project is a delightful example of how to make a website feel "alive" and "handcrafted" using code. It prioritizes **Micro-Interactions** and **Atmosphere** over complex frameworks.

Here is a breakdown of the "Magic" spells implemented in the code.

---

## 🎩 1. The Soot Sprite Logic

Small creatures appear and scurry away as you move the mouse. This is a particle system disguised as a character.

*   **Trigger**: `mousemove` event.
*   **Probability**: `Math.random() < 0.05` ensures they don't appear *every* frame, but just occasionally (5% chance per move event), making them feel rare and alive.
*   **CSS Animation**: We use a `@keyframes scurry` animation that scales the sprite down to 0 while translating it to a random offset (`var(--mx), var(--my)`). This makes them look like they are running into the darkness.

```css
@keyframes scurry {
    0% { transform: scale(1); opacity: 0.8; }
    100% { transform: scale(0) translate(var(--mx), var(--my)); opacity: 0; }
}
```

---

## 🍬 2. Konpeito (Star Candy) Physics

Calculated chaos makes for the best confetti effects.

*   **Trigonometry**: When clicked, we spawn multiple candy elements. To make them explode outward in a circle, we calculate `dx` (delta x) and `dy` (delta y) using `Math.cos(angle)` and `Math.sin(angle)`.
*   **Gravity Hack**: Notice `dy` has an extra `+ 100px`. This adds a "gravity" effect, pulling the candy downward after the initial burst.

---

## 🍂 3. Jelly Physics (CSS Transforms)

How do you make buttons feel soft? By distorting their scale.

*   **Technique**: We use a `scale(x, y)` transform keyframe animation.
*   **Squash and Stretch**:
    *   Scale X goes `1.1` (Wide), Scale Y goes `0.9` (Flat).
    *   Then X goes `0.9` (Thin), Y goes `1.1` (Tall).
    *   This rapid oscillation mimics the physics of jelly or soft bread.

```css
50% { transform: scale(1.1, 0.9); } /* Squash */
75% { transform: scale(0.95, 1.05); } /* Stretch */
```

---

## 🕰️ 4. Time-Shift Logic (SVG & CSS Variables)

The background isn't an image file; it's a dynamic CSS variable system.

*   **Concept**: We don't change 50 different styles manually. We change **CSS Variables** (`--bg-color`, `--text-color`) based on the time.
*   **Day/Night Cycle**:
    *   **Day**: Cream background, Brown text.
    *   **Night**: Dark overlay `opacity: 1`, Lantern logic active.
*   **Lantern**: In Night mode, we use `mix-blend-mode: screen` on a radial gradient following the mouse to "light up" the dark overlay underneath it.

---

## 🐈 5. Scroll Progress Cat

A simple progress bar, but cat-themed.

*   **Math**: `ScrollTop / (ScrollHeight - ClientHeight) * 100` gives us a percentage (0-100%).
*   **Visualization**: Instead of just a bar, we add a `::after` pseudo-element with a cat emoji (`content: '🐈'`) positioned at the right edge of the bar. As the bar width increases, the cat walks forward.

---

## 📚 Extensions to Try

1.  **Golden Evenings**: Add a specific "Sunset" mode between 16:00 and 18:00 with a deep orange/purple gradient overlay.
2.  **Sound Effects**: Add a soft "pop" sound when clicking to spawn Konpeito (using the Web Audio API skills from the Timer app!).
3.  **Seasonal Changes**: Use the `Date()` object to detect the month. If it's December, change the falling leaves to Snowflakes ❄️.

Happy Baking! 🥞
