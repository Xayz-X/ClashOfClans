# Clash of Clans Data Extractor

This project automates the process of downloading, decompressing, and converting Clash of Clans game data files (such as buildings, heroes, pets, troops, spells, and more) into structured JSON files for easy use in bots, tools, or analysis.

## Features

- Downloads the latest game data files directly from Clash of Clans asset servers.
- Supports multiple data types: buildings, characters, heroes, pets, spells, super troops, equipment, town hall levels, and localization texts.
- Handles various compression formats (LZHAM, ZSTD, LZMA) automatically.
- Converts raw CSV data into clean, structured JSON with type conversion and post-processing.
- Cleans up temporary files after processing.

## How It Works

1. **Download**: Fetches the latest data files from the official Clash of Clans asset server using a fingerprint.
2. **Decompress**: Automatically detects and decompresses files using the correct algorithm.
3. **Parse & Convert**: Parses CSV data, handles carry-over logic for blank fields, and converts values to appropriate types (boolean, integer, string).
4. **Post-process**: Moves single-value columns to the top level for easier access.
5. **Save**: Outputs the final structured data as JSON files in the `assets/` directory.

## Usage

1. Install required dependencies:
	```bash
	pip install aiohttp zstandard pylzham
    # or
    uv sync
	```
	(Some modules like `lzma` are included in Python's standard library.)

2. Run the script:
	```bash
	python main.py
	```

3. The processed JSON files will be saved in the `assets/` folder.

## Output Files

- `assets/buildings.json`
- `assets/characters.json`
- `assets/heroes.json`
- `assets/pets.json`
- `assets/spells.json`
- `assets/supers.json`
- `assets/equipment.json`
- `assets/townhall_levels.json`
- `assets/texts_EN.json`

## Customization

- To update the fingerprint (for the latest game data), you can uncomment and use the `get_fingerprint()` function in `main.py`.
- You can add or remove target files by editing the `TARGETS` list in `main.py`.

## Notes

- The script is designed for automation and can be integrated into Discord bots or other tools that require up-to-date Clash of Clans data.