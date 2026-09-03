# Python-Image-Resizer

Command-line Python scripts for resizing images to a specific size in inches (converted to pixels via DPI), with options to resize a single image or an entire folder, and to either force exact dimensions or preserve the original aspect ratio.

## Features

Four standalone scripts, each with a matching packaged executable in `/dist`:

| Script | Executable | Description |
|---|---|---|
| `resizeExactOne.py` | `run-resizeExactOne` | Resizes a single image to an exact width/height in inches, without preserving aspect ratio. |
| `resizeSafeOne.py` | `run-resizeSafeOne` | Resizes a single image to fit within a target width/height in inches, preserving aspect ratio. |
| `resizeExactAll.py` | `run-resizeExactAll` | Resizes every image in a folder to an exact width/height in inches, without preserving aspect ratio. |
| `resizeSafeAll.py` | `run-resizeSafeAll` | Resizes every image in a folder to fit within a target width/height in inches, preserving aspect ratio. |

All resizing uses Lanczos resampling for quality, and target size is entered in inches — the scripts convert this to pixels using the image's DPI (or 96 DPI as a default/assumption when not available).

Supported input formats for the "All" (folder) scripts: `.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`. Output is always saved as `.png`.

## Tech Stack

- **Python 3**
- [`Pillow`](https://pypi.org/project/Pillow/) `9.2.0`

## Prerequisites

- Python 3 (only needed if running from source — the packaged executables in `/dist` require no Python installation)

## Installation

Clone the repository:

```bash
git clone https://github.com/paoradox/Python-Image-Resizer.git
cd Python-Image-Resizer
```

Install dependencies:

```bash
pip install -r requirements.txt
```

## Usage

### Option 1: Run from source

Run the script matching what you need:

```bash
# Resize one image, exact size (no aspect ratio)
python resizeExactOne.py

# Resize one image, preserve aspect ratio
python resizeSafeOne.py

# Resize every image in a folder, exact size (no aspect ratio)
python resizeExactAll.py

# Resize every image in a folder, preserve aspect ratio
python resizeSafeAll.py
```

Each script will prompt you for:
- The path to the image (single-image scripts) or folder (batch scripts)
- The desired width and height, in inches

**Output:**
- Single-image scripts save the result alongside the original as `<original-name>_resizedExact.png` or `<original-name>_resizedSafe.png`.
- Folder scripts save results in the same folder as `resizedExact_image_<n>.png` or `resizedSafe_image_<n>.png`.

### Option 2: Run the packaged executables

Pre-built executables are available in [`/dist`](./dist) — run the one matching your needs directly, no Python installation required:

- `run-resizeExactOne`
- `run-resizeSafeOne`
- `run-resizeExactAll`
- `run-resizeSafeAll`

## Project Structure

```
Python-Image-Resizer/
├── dist/
│   ├── run-resizeExactAll     # Packaged executable
│   ├── run-resizeExactOne     # Packaged executable
│   ├── run-resizeSafeAll      # Packaged executable
│   └── run-resizeSafeOne      # Packaged executable
├── resizeExactAll.py          # Resize all images in a folder, exact size
├── resizeExactOne.py          # Resize one image, exact size
├── resizeSafeAll.py           # Resize all images in a folder, preserve aspect ratio
├── resizeSafeOne.py           # Resize one image, preserve aspect ratio
├── requirements.txt
└── ico.ico                    # App icon
```

## License

Not specified.
