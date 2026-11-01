# Donkey Kong 3 for Atari 5200

DK3-5200 **version 1.2**, for a stock **16 KB NTSC Atari 5200**. This is the
5200 port of DKFAST, developed with OpenAI Codex.

## Downloads

- [DK3-5200-v1.2.car](DK3-5200-v1.2.car) — ready-to-play cartridge with its mapper header.
- [DK3-5200-v1.2.rom](DK3-5200-v1.2.rom) — the same 128 KiB payload without a header.
- [DK3-5200-v1.2-source.zip](DK3-5200-v1.2-source.zip) — full game source, graphics, build tools, tests, and archived validation results.
- [SHA256SUMS.txt](SHA256SUMS.txt) — download checksums.

For a download, open the file and use GitHub's **Download raw file** button.

## Playing

Use controller port 1 and **128 KB Atari 5200 SuperCart banking (CAR type 72)**.
The `.car` header identifies the mapper. Select that mapper manually when
using the raw `.rom` file. This is a banked cartridge, not an ordinary 32 KB image.

Configure an emulator as **Atari 5200, NTSC, 16 KB RAM**, using an original
Atari 5200 BIOS. The game was reported working with the original BIOS in
AltirraSDL; the Altirra replacement 5200 BIOS was reported to crash. BIOS files
are not included.

The game was also confirmed working on A5200PicoCart P2 after its SuperCart
firmware correction. That cartridge firmware is a separate project; a game
ROM update alone does not install the firmware correction.

| Control | Action |
| --- | --- |
| Analog stick | Move left/right; up/down for platform movement and jumping |
| Lower fire | Pump spray; release and press again for another pump |
| START or lower fire at title | Start a game |
| PAUSE | Pause/resume |
| RESET | Return to the title |
| Keypad 1 | Toggle music; sound effects remain enabled |

## Release history

- **1.2:** changes the on-screen version from V0.2 to V1.2, plus the CAR checksum.
  Gameplay and controller handling are unchanged.
- **0.2:** corrects the platform palette boundary, keeping the vines and
  caterpillars above the top platform green.
- **0.1:** initial Atari 5200 port of DKFAST v0.3.

The 1.2 CAR differs from the released 0.2 CAR at exactly two file offsets:
`0x3BA4` (`10` to `11`, the version digit) and `0x0B` (`6D` to `6E`, the checksum).

## Building from source

Unzip the source archive. Install Python 3, Pillow, and cc65 with `cc65`,
`ca65`, and `ld65` on PATH, then run inside the extracted directory:

```sh
python3 -m pip install Pillow
python3 build_release.py
```

The inherited build was tested with Ubuntu's cc65 2.19-1 package (the compiler
reports V2.18). The release wrapper builds the original 0.2 game, verifies its
SHA-256, applies the exact version-only patch, and verifies the released 1.2
SHA-256. A different compiler output is rejected instead of being silently
patched. Outputs are `build/DK3-5200-v1.2.car` and `build/DK3-5200-v1.2.rom`.

The original `README.txt` documents the memory map, renderer, build, and
emulator harness. Its validation statements describe the archived 0.2
development run. `RELEASE-1.2.txt` explains this release's provenance and checks.

## Credits

This is an unofficial homebrew adaptation. Original Donkey Kong 3 characters,
game concepts, and title design are Nintendo's. Port development: OpenAI Codex.
Music: **Monkeys Spinning Monkeys**, Kevin MacLeod, arranged for Atari POKEY,
under Creative Commons Attribution 4.0. Full attribution and music adaptation
details are in [CREDITS.txt](CREDITS.txt).
