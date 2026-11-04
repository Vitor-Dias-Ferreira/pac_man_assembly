# Pac-Man in Assembly

A Pac-Man-style game written from scratch in assembly for a 16-bit load/store RISC processor, created for the course **SSC0955 - Introduction to Computer Systems** at the University of São Paulo (ICMC-USP).

> **Language note:** this was a university assignment in Brazil, so the game's on-screen text and the code comments are in Portuguese. The code was kept as submitted.

**Team:** Vitor Dias and Adryann Olivatti

**Presentation video:** [watch on YouTube](https://youtu.be/I6nawJaza4U?is=p3_5h2Y00fKaRiWZ)

## What we built

- The complete game, written from scratch in assembly.
- A `sound r0, r1, r2` instruction for the simulator, used to add music to the game.

## How to run it

The game runs on the ICMC processor simulator created by Prof. Simões (ICMC-USP), which is not included in this repository. See [his GitHub](https://github.com/simoesusp) for the simulator.

To build a game, write an `.asm` file and use the assembler to convert it into a `.mif` file. In this repository, `pacman.asm` is the source code, and `pacman.mif` and `charmap.mif` are the memory files.

## Audio generation

The audio instruction is blocking, so long notes would freeze the game. To write the melodies without overflowing the buffer or stalling the processor, we used AI-assisted prompting to map note frequencies and durations.

This is the prompt template we used, translated from Portuguese:

```text
Act as an expert in music theory and low-level programming.
Your task is to transcribe a well-known melody into the assembly language of a custom 16-bit academic processor (the ICMC Processor).

### HARDWARE RULES:
1. The simulator has a sound instruction with this exact syntax: `SOUND Rx, Ry, Rz`
2. The parameters are:
   - Rx = Note frequency in hertz (Hz).
   - Ry = Note duration in milliseconds (ms).
   - Rz = Wave type (0 = sine, 1 = square, 2 = triangle, 3 = sawtooth).
3. The SOUND instruction is BLOCKING. To keep the game from freezing, the durations in Ry must be extremely short, preferably between 80 ms and 150 ms at most.

### CODE STRUCTURE:
- Create a subroutine with a descriptive name (e.g., PlayIntroMusic:).
- Push and pop the registers used (r0, r1, r2) at the start and end of the subroutine.
- Load the wave value (Rz) only once at the top to save instructions.
- Use `loadn r0, #<frequency>` and `loadn r1, #<duration>` before calling `SOUND r0, r1, r2` for each note.
```

## Screenshots

### Start screen

<img width="651" height="489" alt="Game start screen" src="https://github.com/user-attachments/assets/af7eb531-6227-4688-9c14-018bba248bde" />

### Game over

<img width="651" height="489" alt="Game over screen" src="https://github.com/user-attachments/assets/7d8fe8f7-804d-482e-94f4-61aa9ab85e70" />

### Ghosts that can be attacked

<img width="651" height="489" alt="Gameplay with ghosts that can be attacked" src="https://github.com/user-attachments/assets/51a3c6ff-40ed-4336-abfb-a2f7b2203d10" />

### Win screen

<img width="651" height="489" alt="Win screen" src="https://github.com/user-attachments/assets/3643d56f-33b2-4559-9f64-610fb693ec99" />
