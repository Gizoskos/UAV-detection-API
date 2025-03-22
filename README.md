# UAV Detection API

This repository contains a Dockerized UAV (Unmanned Aerial Vehicle) Detection System developed using Python, FastAPI, and YOLOv8. The API accepts image or video inputs and returns bounding box detections for UAVs using a trained deep learning model.

---

## Project Context

This project was developed as part of a defense industry simulation. Detecting UAVs in military zones is a critical task for modern defense systems. This API acts as a modular and scalable component that can be integrated into larger UAV monitoring and command infrastructures.

---

## Features

- Object detection using YOLOv8
- FastAPI-based RESTful API
- Upload and detect UAVs from images
- Runs in an isolated Docker container
- Can be deployed locally or to a cloud service supporting containers

---

## Technologies Used

| Layer          | Technology        |
|----------------|------------------|
| Programming    | Python 3.10       |
| API Framework  | FastAPI           |
| Model          | YOLOv8 (Ultralytics) |
| Detection Tools| OpenCV            |
| Containerization | Docker          |

---

## Project Structure

```bash
UAV-detection-API/
├── app.py                 # Main FastAPI application
├── detect.py              # YOLOv8 UAV detection script
├── model/                 # Contains trained YOLOv8 weights (.pt file)
├── Dockerfile             # Docker image definition
├── requirements.txt       # Python dependencies
└── README.md
To view this structure, you can use the tree command:

bash
Copy
Edit
# Linux
sudo apt install tree && tree .

# macOS (Homebrew)
brew install tree && tree .

# Windows (PowerShell)
choco install tree
tree /f
Installation & Setup
1. Clone the Repository
bash
Copy
Edit
git clone https://github.com/Gizoskos/UAV-detection-API.git
cd UAV-detection-API
2. Build the Docker Image
bash
Copy
Edit
docker build -t uav-detection-api .
3. Run the Container
bash
Copy
Edit
docker run -p 8000:8000 uav-detection-api
4. Access the API Docs
Visit: http://localhost:8000/docs
This opens the Swagger UI for testing the /predict endpoint.

API Usage
Endpoint: POST /predict
Payload:
Send an image file (.jpg, .png, etc.) using multipart/form-data.

Example (using curl):

bash
Copy
Edit
curl -X POST "http://localhost:8000/predict" \
     -H "accept: application/json" \
     -H "Content-Type: multipart/form-data" \
     -F "file=@example.jpg"
Response:

json
Copy
Edit
{
  "detections": [
    {
      "x1": 134.0,
      "y1": 122.0,
      "x2": 304.5,
      "y2": 201.5
    }
  ]
}
Dependencies
Install required libraries manually if running outside Docker:

bash
Copy
Edit
pip install -r requirements.txt
requirements.txt includes:

nginx
Copy
Edit
fastapi
uvicorn
ultralytics
opencv-python
python-multipart
Conclusion
This project demonstrates a lightweight and containerized solution for UAV detection using YOLOv8 and FastAPI. By packaging the model and API inside a Docker container, it allows for consistent and isolated deployment across environments. The system is ideal as a modular detection service for larger defense infrastructure or simulation environments.

