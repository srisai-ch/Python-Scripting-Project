# Python-Scripting-Project

A small utility that finds "game" directories inside a data tree, copies them to a new `games` directory (removing the game suffix), compiles each game's Go source, and produces a JSON metadata file describing the games.

## What this project does

- Scans a source `data` directory for subdirectories whose names contain the pattern `_game`.
- Copies each found game directory into a new target `games` directory, removing the `_game` suffix from the folder name.
- Finds the single `.go` source file inside each game directory, compiles it with `go build`.
- Writes a `games_metadata.json` file in the target directory that lists the games and a count.

## Assumptions

- Each game is stored in a directory whose name contains `_game`.
- Each game directory contains exactly one `.go` file that must be compiled.
- The script is run from the project root.

## Requirements

- Python 3.8+ (run `python --version`)
- Go toolchain installed and available on PATH (`go build`)

## Usage

1. From the project root, run:

   ```sh
   python get_game_data.py data games
   ```

   - `data` is the source folder to scan
   - `games` is the target folder to create/populate

2. Result:
   - A `games` directory with cleaned game folders
   - A `games_metadata.json` file inside `games`
   - Each game compiled using `go build` (binary created in the game folder)

## License

- No license specified.
