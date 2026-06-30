# Snake Clone (Unity)

A 2D grid-based Snake clone built with Unity 2022.3 as a personal learning project.

> Replace this line with a screenshot or short GIF once you have one.

---

## About the Game

Classic snake, pixel-art style. You control a growing snake on a fixed grid: eat apples to grow, avoid hitting the walls and your own body, and beat your best score.

The main goal of this project was to practice:

- Clean scene and script organization
- Grid-based movement with a direction input buffer
- Dynamic sprite rotation for body segments (straight vs. curved on turns)
- Animator-driven feedback (idle, blink, open/close mouth)
- Persistent high scores per difficulty
- Full UI flow: Main Menu, Pause, Game Over, restart

---

## Features

- Grid-based snake movement, one cell per tick
- Direction input buffer for responsive turns
- Growing body with automatic curved-segment sprite swap on turns
- Animated head: idle, periodic blink, open/close mouth when food is near
- Three difficulty levels: Easy, Medium, Hard
- Persistent high score per difficulty (PlayerPrefs)
- Volume slider and difficulty selector in the main menu
- Pause menu, game over screen with high-score feedback
- Wrap-around bounds on Easy, hard wood walls on Medium and Hard
- Random food spawning with safe distance from walls
- Pixel-art sprites and sound feedback (bite, beep, impact)

---

## Tech Stack

- Engine: Unity 2022.3.33f1
- Render Pipeline: Universal Render Pipeline (URP)
- Language: C#
- UI: TextMesh Pro
- Audio: Unity AudioSource (mp3 + wav)

---

## Controls

| Action                          | Key    |
| ------------------------------- | ------ |
| Move Up                         | W      |
| Move Down                       | S      |
| Move Left                       | A      |
| Move Right                      | D      |
| Pause (during play)             | Esc    |
| Restart (after Game Over)       | Enter  |
| Back to Menu (after Game Over)  | Esc    |

---

## How to Run

### Open in Unity
1. Clone the repository:
   ```bash
   git clone https://github.com/P4TTT0/Unity-Snake-Clone.git
   ```
2. Open Unity Hub.
3. Click "Add project" and select the `Snake/` folder (the actual Unity project).
4. Press Play in the Unity Editor.

### Build
The project is configured for Windows. To produce a build:
1. Open the project in Unity.
2. Open File > Build Settings.
3. Add the `MainMenu` and `SnakeScene` scenes (if not already included).
4. Select your target platform and click Build.

> No public WebGL or itch.io build is available for this project.

---

## Difficulty Levels

| Difficulty | Walls                  | Speed   | Notes                       |
| ---------- | ---------------------- | ------- | --------------------------- |
| Easy       | Wrap around the screen | Normal  | Best for casual play        |
| Medium     | Hard wood walls        | Normal  | Standard challenge          |
| Hard       | Hard wood walls        | 2x      | For speedrun practice       |

High scores are saved independently per difficulty.

---

## Project Structure

The Unity project lives inside `Snake/`. Code is grouped by responsibility under `Assets/Scripts/`:

```
Snake/Assets/
├── Animations/    # Animator controllers + animation clips
├── Prefabs/       # SnakeBodyPrefab, SnakeTail
├── Scenes/        # MainMenu, SnakeScene
├── Scripts/
│   ├── Enums/     # DifficultyType
│   ├── Functions/ # PrefsUtils, VectorUtils
│   ├── Game/      # Snake, Food, GameManager, SnakeBlink
│   ├── Screen/    # MainMenu, PauseMenu, GameOverScreen
│   └── Settings/  # GameSettings (static shared state)
├── Sounds/        # beep, bite, impact
├── Sprites/       # Pixel art snake and apple
└── Text/          # Fonts + colors
```

Key scripts:

- `Snake.cs` - movement, body growth, sprite rotation, collision, mouth state
- `GameManager.cs` - score, high score persistence, game over handling
- `Food.cs` - random spawn inside the play area
- `SnakeBlink.cs` - periodic blink animation
- `MainMenu.cs` / `PauseMenu.cs` / `GameOverScreen.cs` - UI flow

---

## Learning Notes

This project was built step-by-step as part of a personal Unity roadmap. Main focus:

- Folders grouped by responsibility (Game, Screen, Settings, Functions, Enums)
- Reusable UI panels (Main Menu, Pause, Game Over)
- Static `GameSettings` for shared state instead of singletons
- Animator triggers instead of hardcoded sprite swaps
- `PrefsUtils` wrapper around PlayerPrefs for safe high-score persistence
- Direction buffer to avoid losing inputs on quick turns

---

## License

This repository is shared for learning and portfolio purposes only. You are free to explore the code for personal study. Please do not redistribute the art assets for commercial use.

---

## Author

Made by P4TTT0
- GitHub: https://github.com/P4TTT0
- itch.io: https://p4ttt0.itch.io/
