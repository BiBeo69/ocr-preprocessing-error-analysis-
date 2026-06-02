# OCR Preprocessing & Error Analysis

A personal Computer Vision mini-project exploring how simple image preprocessing techniques affect OCR performance across different image-quality conditions.

## Project Overview

This project simulates an introductory OCR evaluation workflow:

1. Collect a small image set containing text under different visual conditions.
2. Apply preprocessing techniques using OpenCV.
3. Run OCR before and after preprocessing using Tesseract.
4. Compare OCR outputs and identify failure cases.
5. Test targeted improvements for problematic image groups.

## Dataset

The evaluation set contains 10 text-containing images across five conditions:

| Image Condition  | Number of Images |
| ---------------- | ---------------: |
| Clear            |                3 |
| Tilted           |                3 |
| Dark             |                1 |
| Blurred          |                1 |
| Noisy Background |                2 |

No sensitive personal documents were used.

## Processing Pipeline

```text
Input Image
→ Resize
→ Grayscale Conversion
→ Otsu Thresholding
→ OCR with Tesseract
→ Manual Error Analysis
→ Targeted Improvement Trial
```

Additional targeted techniques tested:

* Adaptive Thresholding for dark and noisy-background cases.
* Sharpening for the blurred-image case.

## Main Findings

* Otsu thresholding did not consistently improve OCR performance across all image types.
* Clear images generally performed well without heavy preprocessing.
* Thresholding degraded OCR results for several dark and noisy-background inputs.
* Adaptive Thresholding did not improve the selected dark/noisy-background cases under the tested configuration.
* Sharpening improved the blurred-image case by recovering the main title text correctly as `SCHOOL TRANSCRIPT`, while the original OCR failed and the Otsu output misread the word `SCHOOL`.

## Technical Stack

* Python
* Google Colab
* OpenCV
* Tesseract OCR / pytesseract
* Pandas
* Matplotlib

## Repository Structure

```text
.
├── ocr_preprocessing_analysis.ipynb
├── input_images/
├── output_images/
│   ├── grayscale/
│   ├── otsu_threshold/
│   ├── adaptive_threshold/
│   └── sharpening/
└── observations/
```

## Key Lesson

Image preprocessing should not be applied uniformly. A technique that improves one failure case may degrade another. OCR quality should therefore be evaluated directly on model outputs rather than inferred only from visual appearance.

## Limitations

* The dataset is small and manually collected.
* Evaluation was mainly qualitative rather than based on character error rate or word error rate.
* Tesseract was used as a baseline OCR engine and does not represent a production OCR system.
* More advanced techniques such as deblurring, deskewing, document layout analysis, and learned OCR models were not explored.

## Notes

This is a personal learning project completed as preparation for an AI internship. It is not affiliated with any company.
