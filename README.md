# Medical_Text_Extractor

Medical Report Extractor
This project is a Python-based tool designed to extract text and structured data from medical reports in PDF or image formats (JPG, PNG, JPEG). It uses the Qwen2.5-VL-7B-Instruct model for OCR and text processing, classifies report types, and outputs structured JSON files. The tool is optimized for medical reports and supports both text-based and image-based PDFs.
Features

Text Extraction: Extracts text from images and PDFs using OCR with the Qwen2.5-VL-7B-Instruct model.
Report Classification: Identifies the type of medical report (e.g., Laboratory Test, Imaging, Discharge Summary).
Structured JSON Output: Converts extracted text into structured JSON, preserving tables and hierarchies.
Image Preprocessing: Enhances images for better OCR accuracy using OpenCV and Pillow.
Support for Multiple Formats: Processes text-based PDFs, image-based PDFs, and standalone images.

Prerequisites

Python 3.8+
CUDA-compatible GPU (optional, for faster processing)
Poppler-utils (for PDF-to-image conversion)

Installation

Clone the Repository:
git clone https://github.com/your-username/medical-report-extractor.git
cd medical-report-extractor


Install Dependencies:Ensure you have pip installed, then run:
pip install torch torchvision transformers pdfplumber pymupdf pillow opencv-python pdf2image bitsandbytes
pip install -q git+https://github.com/huggingface/transformers.git@1931a351408dbd1d0e2c4d6d7ee0eb5e8807d7bf
pip install -q qwen-vl-utils accelerate huggingface_hub ipywidgets


Install Poppler (for PDF-to-image conversion):

On Ubuntu/Debian:sudo apt-get install poppler-utils -y


On macOS:brew install poppler


On Windows, download and install Poppler from a trusted source and add it to your system PATH.



Usage

Prepare Input Files:Place your PDF or image files (.pdf, .jpg, .png, .jpeg) in the dataset directory.

Run the Script:Execute the main script to process all files in the dataset directory:
python main.py


Output:

Extracted text and structured JSON files are saved in the output directory.
For PDFs, each page is processed separately, with outputs named as {filename}_page_{n}_structured.json.


Example:For a file report.pdf in the dataset directory, the script will generate:

output/report_page_1_structured.json (structured JSON for page 1)
Similar files for additional pages or images.



Code Structure

main.py: Main script to process input files and generate outputs.
dataset/: Directory for input PDF/image files.
output/: Directory for output text and JSON files.
Functions:
is_text_pdf(): Checks if a PDF is text-based or image-based.
clean_image(): Enhances images for better OCR accuracy.
run_qwen_ocr(): Performs OCR using the Qwen2.5-VL-7B model.
classify_report_type(): Identifies the medical report type.
generate_structured_json(): Converts OCR text into structured JSON.
process_input_file(): Main function to handle file processing.



Requirements
The script uses the following Python packages:

torch, torchvision: For GPU acceleration and model loading.
transformers: For the Qwen2.5-VL-7B-Instruct model.
pdfplumber, pymupdf: For PDF text extraction.
pillow, opencv-python: For image processing.
pdf2image: For converting PDFs to images.
bitsandbytes: For 4-bit quantization to optimize model performance.
qwen-vl-utils, accelerate, huggingface_hub: For model utilities and compatibility.

Notes

GPU Usage: The script automatically uses CUDA if available. Ensure your system has a compatible GPU and drivers.
Memory Management: The script includes clear_gpu_memory() to manage GPU memory during processing.
Model: The Qwen2.5-VL-7B-Instruct model is loaded with 4-bit quantization for efficiency.
Input Directory: Ensure the dataset directory exists and contains valid input files.
Error Handling: Unsupported file formats are skipped with a warning message.

Contributing
Contributions are welcome! Please submit a pull request or open an issue for suggestions or bug reports.
License
This project is licensed under the MIT License. See the LICENSE file for details.
Contact
For questions or support, please open an issue on GitHub or contact [your-email@example.com].
