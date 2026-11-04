# Handwriting English to Hindi Translator

Python desktop application for recognizing handwritten English from images and translating the recognized text into Hindi.

## Features
- OpenCV image preprocessing
- Microsoft TrOCR handwriting recognition
- Argos Translate English-to-Hindi translation
- Tkinter desktop interface
- Export recognized and translated text to TXT and Hindi PDF

## Setup
Use Python 3.10–3.12 and create a virtual environment.

```bash
python -m venv .venv
# Windows:
.venv\\Scripts\\activate
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
python install_argos_model.py
python main.py
```

The first OCR run downloads the TrOCR model unless it is already cached locally. For fully offline use, download/cache the model and Argos language package before disconnecting from the internet.

## Hindi PDF font
Set `HINDI_FONT_PATH` to a Devanagari TrueType font file if Mangal is not available. For example, on Windows:

```powershell
$env:HINDI_FONT_PATH="C:\\Windows\\Fonts\\mangal.ttf"
```

PDF Devanagari shaping can vary with ReportLab/font support. Verify the generated PDF on your target system.

## Project structure
```text
app/
  config.py
  gui.py
  image_preprocessor.py
  line_segmenter.py
  ocr_engine.py
  pdf_generator.py
  translator_engine.py
  utils.py
main.py
install_argos_model.py
requirements.txt
```

## Notes
TrOCR is designed for handwritten text lines. The line segmentation stage is a heuristic and may need adjustment for tightly spaced or irregular handwriting. Compare results against the original image when OCR accuracy matters.
