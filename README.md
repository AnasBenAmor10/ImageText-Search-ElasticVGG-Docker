
# 📦 Image and Text Search Engine with VGG16, Elasticsearch, FastAPI, Streamlit, and Logstash

This project is a high-performance **image and text search engine** leveraging **deep learning** and modern search technology. It uses the **VGG16** model for feature extraction from images and **Elasticsearch** for fast indexing and retrieval of data. A seamless backend API is provided with **FastAPI**, a user-friendly frontend interface with **Streamlit**, and **Logstash** is used for efficient data ingestion.

---

## 📂 **Project Architecture**


## 🚀 **How It Works**

### 1. **VGG16 Feature Extraction**  
- Uses the **VGG16 deep learning model** to extract high-level **feature vectors** from uploaded images.  
- These vectors represent images in a meaningful way, capturing important features like texture, color, and shape.

### 2. **Elasticsearch Integration**  
- Indexes both **image features and textual data** using **Elasticsearch**, ensuring **fast and accurate** search results with similarity matching. 

### 3. **FastAPI Backend**  
- Provides a **RESTful API** using **FastAPI** for handling search requests.  
- Users can query by **text** or **images** and receive relevant results from Elasticsearch.

### 4. **Streamlit Web Interface**  
- **Streamlit** provides an intuitive **web interface**, enabling users to upload images, enter search queries, and explore the results. 

### 5. **Logstash Data Ingestion**  
- **Logstash** automates the ingestion of **CSV files** and other structured data into Elasticsearch, streamlining the search process with up-to-date indexes.

---

## 📸 **Features**

- **Image Similarity Search**: Upload an image to find visually similar ones.
- **Text-based Search**: Perform searches with keywords or descriptions.
- **Deep Learning with VGG16**: Extract feature vectors for high-accuracy searches.
- **FastAPI Backend**: Offers fast and reliable API endpoints.
- **Interactive UI with Streamlit**: User-friendly frontend for easy interaction.
- **Automated Data Ingestion**: Logstash ensures up-to-date and organized data.

---

## 🛠️ **Technology Stack**

| Component         | Technology    |
|-------------------|---------------|
| **Feature Extraction** | VGG16 (Keras) |
| **Search Engine**     | Elasticsearch |
| **Backend API**       | FastAPI       |
| **Frontend Interface**| Streamlit     |
| **Data Ingestion**    | Logstash      |
| **Containerization**  | Docker        |

---


## 🔧 **How to Run the Project**

### Prerequisites  
- Docker and Docker Compose installed on your machine.
- Ensure all dependencies listed in the `requirements.txt` files are properly configured.

### 1. **Clone the Repository**

```bash
git clone <repository-url>
cd <repository-name>
```

### 2. **Navigate to the Infra Folder**

```bash
cd infra
```

### 3. **Build and Run the Project using Docker Compose**

```bash
docker-compose up --build
```
### 4. **Manually Run the Frontend and Backend** 
#### 4.1 Run the Streamlit Frontend
```bash
cd Frontend
streamlit run app.py
```
Access the Streamlit web interface at http://localhost:8501.

#### 4.2 Run the FastAPI Backend
```bash
cd Backend
uvicorn route:app --reload
```

### 5. **Access the Web Interface and API**  
- **Frontend (Streamlit):** Open [http://localhost:8501](http://localhost:8501).  
- **Backend API (FastAPI):** Visit the Swagger docs at [http://localhost:8000/docs](http://localhost:8000/docs).

---

## 📂 **Folder Structure**

**Backend**
The Backend directory contains the core components of the backend service, responsible for data ingestion, feature extraction, and API routing.


```
├── backend.config.py        # Configuration settings for the backend service
├── ingest_data_elastic.py   # Script to ingest data into Elasticsearch
├── feature_extractor.py      # Module for extracting features from the ingested data
├── route.py                  # Defines the API routes and endpoints for the backend service
```
**Frontend**
The Frontend directory includes the Streamlit application for user interaction.

```
├── app.py                    # Main entry point for the Streamlit frontend application
```
**Infra**
The infra directory manages the infrastructure setup, including Docker configurations and service orchestration.

```
├── docker-compose.yml        # Docker Compose file to define and run multi-container Docker applications
│
├── elastic                   # Directory containing Elasticsearch related files
│   ├── create_index.py       # Script to create indices in Elasticsearch
│   ├── custom_cmd.sh         # Custom command script for initializing the Elasticsearch service
│   └── Dockerfile.elastic     # Dockerfile to build the Elasticsearch image
│
├── logstash                  # Directory containing Logstash related files
│   ├── Dockerfile.logstash    # Dockerfile to build the Logstash image
│   └── pipeline               # Directory for Logstash pipeline configurations
│       └── logstash.conf      # Configuration file defining the Logstash pipeline
```
---

## 🛡️ **Environment Variables** 
To ensure the proper functioning of the search engine, set the following environment variables:

Elasticsearch Configuration:

```bash
elastic_url="http://localhost:9200"
elastic_usr="username"
elastic_pass="passwd"

Index Names:

index_name="images"
index_text="flickrphotos"

Paths for Data and Datasets:

datasetPath="../infra/data/mirflickr25k/mirflickr"
dataPath="../infra/data/images"
csvPath="dataset/photo_metadata.csv"

Search Threshold:

threshold=0.2
```
---
## ⚙️ **How the Components Work Together**

- **VGG16 Feature Extraction:** Converts uploaded images into numerical vectors.  
- **Elasticsearch:** Stores these vectors and enables efficient similarity matching.  
- **FastAPI:** Handles API calls from the frontend and interacts with Elasticsearch.  
- **Streamlit:** Offers an interactive interface for users to upload images and view results.  
- **Logstash:** Automates the ingestion of structured data into Elasticsearch.

---
