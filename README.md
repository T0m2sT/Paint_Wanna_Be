# PaintWannaBe

A command-line image editor written in C++17. It loads and saves PNG images and applies a set of geometric and pixel-level transforms — crop, resize, rotate, mirror, fill, replace, invert, grayscale, and more — driven by a small custom scripting language called a **scrim**.

![Grade](https://img.shields.io/badge/Grade-19.8%2F20-1E90FF?style=for-the-badge&labelColor=21262d)
![Course](https://img.shields.io/badge/Course-P-1E90FF?style=for-the-badge&labelColor=21262d)
![Year](https://img.shields.io/badge/Year-2024%2F25-1E90FF?style=for-the-badge&labelColor=21262d)

## How it works

A scrim is a plain-text script listing a sequence of image commands, executed in order:

```
blank 400 400 255 0 0
chain scrims/more-scrims/start1.scrim end
save output/chain1.png
```

Commands can create a blank canvas, open an existing PNG, apply transforms, chain other scrim scripts together, and save the result. Available commands include:

`open`, `save`, `blank`, `crop`, `resize`, `move`, `slide`, `add`, `fill`, `replace`, `invert`, `to_gray_scale`, `h_mirror`, `v_mirror`, `rotate_left`, `rotate_right`, `scaleup`, `chain`

## Build & Run

**Requirements:** C++17 compiler, CMake 3.15+

```bash
cmake -B build
cmake --build build
./build/RunScrim scrims/chain1.scrim
```

Multiple scrims can be passed at once and are run sequentially.

## Project Structure

- **include/**, **src/** — core image model (`Image`, `PNG`, `Color`), command implementations, and the scrim parser
- **scrims/** — sample scrim scripts covering each command and combinations of them
- **input/**, **expected/** — sample PNG inputs and expected outputs used for testing
- **main/** — `RunScrim.cpp` (CLI entry point) and `Tester.cpp` (test runner comparing output against `expected/`)
