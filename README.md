# OCR Application

This project is a FastAPI-based application for Optical Character Recognition (OCR). It allows users to upload images and extract text from them using Tesseract OCR.

## Features
- Upload images via API.
- Extract text from uploaded images.
- Debugging support with `debugpy`.

## Prerequisites
- Python 3.12 or higher
- Docker and Docker Compose (optional for containerized deployment)
- Tesseract OCR installed (if running locally)

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/turahe/ocr-app.git
cd ocr-app
```

### 2. Install Dependencies
#### Using Virtual Environment
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt
```

#### Using Docker
Build the Docker image:
```bash
docker-compose build
```

#### Using Docker Hub
Pull the prebuilt Docker image from Docker Hub:
```bash
docker pull turahe/ocr-app:latest
```

Run the Docker container:
```bash
docker run -d --name ocr-app -p 4000:4000 turahe/ocr-app:latest
```

The application will be available at `http://localhost:4000`.

### 3. Run the Application
#### Locally
```bash
export APP_PORT=5000  # Set the application port (default is 4000)
uvicorn main:app --host 0.0.0.0 --port $APP_PORT --reload
```

#### Using Docker
```bash
APP_PORT=5000 docker-compose up
```

The application will be available at `http://localhost:5000` (or the port you set).

### 4. Debugging
To enable debugging, set the `DEBUG` environment variable to `1`:
```bash
export DEBUG=1  # On Windows: set DEBUG=1
```

### 5. API Endpoints
- `GET /` - Returns a welcome message.
- `GET /hello/{name}` - Greets the user by name.
- `POST /upload-image/` - Upload an image and extract text.

### 6. Extract Text from Images
You can use the `read_image_to_text.py` script to extract text from an image:
```bash
python read_image_to_text.py <image_path>
```

### 7. Deployment
The project includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) for building and deploying the Docker image. Update the secrets in your repository to configure deployment.

## License
This project is licensed under the MIT License.

`