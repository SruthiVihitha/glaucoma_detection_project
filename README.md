# glaucoma_detection_project
This project detects glaucoma from OCT reports using an end-to-end pipeline. A Django backend extracts key metrics via OCR and predicts glaucoma with an ensemble deep learning model. A Streamlit dashboard displays GradCAM heatmaps for visual interpretability.

# Glaucoma Detection from OCT Reports

This project is a comprehensive solution for detecting glaucoma from OCT (Optical Coherence Tomography) reports. It integrates:

- **Django Backend**: Manages file uploads, performs OCR, extracts key metrics, and uses an ensemble deep learning model for glaucoma detection.
- **TensorFlow Models**: An ensemble model combining ResNet50, InceptionV3, MobileNet, and a placeholder SENet (using ResNet50) to predict glaucoma.
- **GradCAM Heatmap Generation**: Provides visual explanations of the model’s predictions.
- **Streamlit Frontend**: Offers an interactive interface for uploading OCT images and visualizing prediction results and heatmaps.

## Repository Structure

```
glaucoma_project/
├── README.md
├── requirements.txt
├── manage.py
├── glaucoma_project/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── reports/
│   ├── __init__.py
│   ├── admin.py
│   ├── forms.py
│   ├── models.py
│   ├── predictor.py
│   ├── serializers.py
│   ├── urls.py
│   └── views.py
└── dashboard_app/
    └── dashboard_app.py
```

## Features

- **OCR Extraction**: Uses [pytesseract](https://github.com/madmaze/pytesseract) to extract text from OCT report images.
- **Metric Extraction**: Parses extracted text using regular expressions to obtain parameters like:
  - Minimum GCL and IPL (OD/OS)
  - Average GCL IPL (OD/OS)
  - Vertical CDR (OD/OS)
  - Rim area (OD/OS)
- **Glaucoma Prediction**: Uses an ensemble deep learning model to predict whether glaucoma is detected.
- **GradCAM Heatmaps**: Generates GradCAM, GradCAM+, and GradCAM++ heatmaps for visual interpretation.
- **Interactive Dashboard**: A Streamlit app that allows users to upload images and view predictions and heatmaps.

## Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/glaucoma_project.git
cd glaucoma_project
```

### 2. Create and Activate a Virtual Environment

- **On Windows:**

  ```bash
  python -m venv glaucoma_project_env
  .\glaucoma_project_env\Scripts\activate
  ```

- **On macOS/Linux:**

  ```bash
  python -m venv glaucoma_project_env
  source glaucoma_project_env/bin/activate
  ```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up Django

- Apply migrations:

  ```bash
  python manage.py makemigrations
  python manage.py migrate
  ```

- (Optional) Create a superuser for the admin panel:

  ```bash
  python manage.py createsuperuser
  ```

### 5. Run the Django Server

```bash
python manage.py runserver 0.0.0.0:8001
```

### 6. Run the Streamlit Dashboard

In a separate terminal (with the virtual environment activated):

```bash
streamlit run dashboard_app/dashboard_app.py
```

## Usage

1. **Upload an OCT Report**:  
   Open the Streamlit dashboard in your browser, upload an OCT report image, and click **Analyze**.

2. **View Results**:  
   The dashboard will display:
   - The glaucoma prediction ("Glaucoma Detected" or "No Glaucoma")
   - GradCAM-based heatmaps for visual interpretation of the model's decision.
   - (Additional extracted metrics can be further integrated if needed.)

## Configuration

- **Tesseract**:  
  Ensure that Tesseract OCR is installed on your system. Update the `TESSERACT_PATH` in `glaucoma_project/settings.py` if needed.

- **Model Architecture**:  
  The ensemble model uses pre-trained weights from ImageNet for ResNet50, InceptionV3, and MobileNet. The SENet branch uses a placeholder implementation based on ResNet50. Adjust the architecture or load custom weights as needed for your application.

## License

This project is licensed under the [MIT License](LICENSE).

## Contact

For any questions, suggestions, or issues, please open an issue in this repository or contact sruthivihitha_potluri@srmap.edu.in.
```

---

Feel free to adjust any details in the README (such as repository URL, contact information, or specific configuration instructions) to match your project's specifics. This file will give users a clear understanding of what the project does, how to set it up, and how to use it.
