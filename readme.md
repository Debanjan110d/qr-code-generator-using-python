
# QR Code Generator using Python 🐍

A versatile QR code generator written in Python. Choose between a simple **command‑line interface** (`main.py`) or a lightweight **Flask web app** (`index.py`). It generates high‑contrast, WCAG‑compliant QR codes for any text or URL.

---

## 🔍 Table of Contents

- [Features](#features)  
- [Prerequisites](#prerequisites)  
- [Installation](#installation)  
- [Usage](#usage)  
  - [Command‑Line (CLI)](#command‑line-cli)  
  - [Web App (Flask)](#web‑app-flask)  
- [Code Overview](#code-overview)  
- [Customization](#customization)  
- [Troubleshooting](#troubleshooting)  
- [Contributing](#contributing)  
- [License](#license)  

---

## Features

- **Dual interfaces**  
  - **CLI**: Quickly generate QR codes via terminal input.  
  - **Web App**: Fill in a form in your browser and download the QR code.  
- **High‑contrast color pairs**  
  - Automatically picks random foreground/background colors with contrast ratio ≥ 4.5 (WCAG) for accessibility.  
- **Configurable options**  
  - QR version, error correction, box size, border.  
- **Minimal dependencies**  
  - `qrcode`, `Pillow`, `Flask` (for web), plus Python’s standard library.

---

## Prerequisites

- Python **3.7+**  
- **pip** (Python package installer)

The following Python packages are required:

```bash
pip install qrcode pillow flask
````

---

## Installation

1. **Clone this repository**

   ```bash
   git clone https://github.com/Debanjan110d/qr-code-generator-using-python.git
   cd qr-code-generator-using-python
   ```
2. **Install dependencies** (see Prerequisites).

---

## Usage

### Command‑Line (CLI)

1. Run the script:

   ```bash
   python main.py
   ```
2. When prompted, enter your text or URL.
3. The script generates a file named
   `qr_code_<URL‑or‑text‑encoded>.png` in the current directory.

Example:

```bash
Enter the link: https://example.com
# → qr_code_https%3A%2F%2Fexample.com.png
```

---

### Web App (Flask)

1. Start the Flask server:

   ```bash
   python index.py
   ```
2. Open your browser to [http://127.0.0.1:5000/](http://127.0.0.1:5000/).
3. Enter your link/text in the form and hit **Generate QR Code**.
4. The QR code image will be sent for download.

---

## Code Overview

### Shared Utility: `generate_qr_code(data, filename)`

* Initializes a `qrcode.QRCode` object with:

  * `version=1`, `error_correction=H`, `box_size=10`, `border=4`.
* Chooses random `(R,G,B)` pairs until the WCAG contrast ratio ≥ 4.5.
* Renders and saves the image to `filename`.

### `main.py`

* Imports only the QR utility and standard modules.
* Prompts the user for input.
* Saves the generated PNG in the working directory.

### `index.py`

* Builds a minimal Flask app.
* Defines a single route (`/`) handling GET (form) and POST (generation).
* Uses `urllib.parse.quote_plus()` to safely encode filenames.
* Returns the PNG directly via `send_file()`.

---

## Customization

* **Change QR version**: adjust `version` or allow user input.
* **Modify error correction**: use `ERROR_CORRECT_L`, `M`, `Q`, or `H`.
* **Alter colors**: tweak or remove the contrast loop for static colors.
* **Box size & border**: change `box_size` and `border` parameters.
* **Add logos**: composite with PIL after generation.
* **Support SVG**: use `qrcode.image.svg.SvgImage` factory.

---

## Troubleshooting

* **ModuleNotFoundError**

  * Ensure you’ve run `pip install qrcode pillow flask`.
* **PermissionError** saving files

  * Run in a writable directory or choose an absolute path.
* **Flask not starting**

  * Check that no other service is bound to port 5000, or set `app.run(port=YOUR_PORT)`.

---

## Contributing

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/YourIdea`)
3. Commit your changes (`git commit -m "Add awesome feature"`)
4. Push to remote (`git push origin feature/YourIdea`)
5. Open a Pull Request

---

## License

This project is released under the **MIT License**. See [LICENSE](LICENSE) for details.

Happy coding & QR‑ing! 🚀

```
::contentReference[oaicite:0]{index=0}
```
