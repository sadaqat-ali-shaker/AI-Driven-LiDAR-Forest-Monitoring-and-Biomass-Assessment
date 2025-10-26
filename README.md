# **Software Requirements Specification (SRS)**  
**Project Title:** Forest Biomass Estimation and Monitoring System  
**Date:** October 2025  

---

## **1. Introduction**

### **1.1 Purpose**
The purpose of this document is to define the functional and non-functional requirements for the **Forest Biomass Estimation and Monitoring System**.  
The system aims to process drone, satellite, or mobile data to identify trees, estimate biomass, detect temporal changes, and generate visual and analytical reports to support environmental management and reforestation planning.

### **1.2 Scope**
The system provides a complete end-to-end workflow for aerial data processing, analysis, and visualization.  
It converts imagery into 3D point clouds, performs feature extraction and biomass estimation, and produces visual dashboards and reports.  

**Key functionalities include:**
- Tree identification and segmentation from point cloud data.  
- Biomass computation using allometric models.  
- Change detection and comparative analysis across time periods.  
- Visualization through dashboards and report generation.  
- Suggested plant/no-plant area recommendations.  

### **1.3 Objectives**
- Automate biomass estimation from aerial imagery.  
- Enable researchers to visualize forest data in real-time.  
- Detect environmental and deforestation changes efficiently.  
- Provide a scalable, modular architecture for future expansion.  

### **1.4 Definitions, Acronyms, and Abbreviations**

| **Term** | **Definition** |
|-----------|----------------|
| **PCD** | Point Cloud Data |
| **RGB** | Red, Green, Blue (image color channels) |
| **API** | Application Programming Interface |
| **UI** | User Interface |

---

## **2. Overall Description**

### **2.1 Product Perspective**
The system operates as a multi-layered architecture combining data processing, storage, and visualization modules.  
It can integrate with drone and satellite platforms for data input and generate comprehensive reports for researchers and environmental agencies.

### **2.2 Product Features**
- Import aerial RGB images and PCD files.  
- Convert RGB data into 3D point clouds.  
- Clean and preprocess datasets for tree extraction.  
- Identify trees, compute biomass, and store metadata.  
- Compare results across time for change detection.  
- Generate analytical dashboards and reports.  

### **2.3 User Characteristics**

| **User Type** | **Description** |
|----------------|-----------------|
| **Researcher** | Uploads data, views analysis, and downloads reports. |
| **Administrator** | Manages users, datasets, and report outputs. |

---

## **3. System Features**

### **3.1 Data Input & Conversion**
- Accepts RGB imagery and point cloud data from drones/satellites.  
- Performs RGB-to-Point Cloud Conversion.  
- Validates and formats input data for consistency.  

### **3.2 Preprocessing and Cleaning**
- Removes noise and separates ground/non-ground points.  
- Normalizes datasets for feature extraction.  

### **3.3 Tree Segmentation & Feature Extraction**
- Identifies tree canopies and trunks from PCD.  
- Extracts geometric features (height, diameter, crown size).  

### **3.4 Biomass Estimation**
- Applies allometric models for per-tree and per-plot biomass.  
- Stores outputs in a structured database.  

### **3.5 Temporal Change Detection**
- Compares two or more datasets from different time periods.  
- Identifies deforestation, growth, or degradation areas.  

### **3.6 Visualization and Reporting**
- Displays maps, charts, and statistical summaries.  
- Exports PDF and CSV reports.  
- Suggests reforestation (plant/no-plant) zones.  

---

## **4. System Design**

### **4.1 Selected Design**
The proposed system follows a **Four-Tier Layered Architecture**, dividing the system into **User**, **Data Input & Conversion**, **Processing**, and **Application/Database Management** layers.  
This design ensures scalability, modularity, and maintainability.

### **4.2 Layered Architecture Overview**
1. **User Layer**  
   - Provides the main interface for interaction (Dashboard).  
   - Allows users to upload data, trigger processing, and view reports.  

2. **Data Input & Conversion Layer**  
   - Manages input data (RGB, PCD).  
   - Converts RGB images into point cloud format.  

3. **Processing Layer**  
   - Handles preprocessing, segmentation, biomass estimation, and change detection.  
   - Communicates with the database for data storage and retrieval.  

4. **Application & Database Management Layer**  
   - Hosts visualization dashboards and report generation modules.  
   - Manages database operations and metadata indexing.  

### **4.3 System Architecture Diagram**
[ User Layer ]
↓
[ Data Input & Conversion Layer ]
↓
[ Processing Layer ]
↓
[ Application & Database Management Layer ]


### **4.4 Justification for Selected Design**

| **Aspect** | **Reason** |
|-------------|------------|
| **Scalability** | Each layer can be updated or scaled independently. |
| **Modularity** | Separation of concerns simplifies maintenance. |
| **Security** | Data access is routed securely via the backend. |
| **Performance** | Supports large dataset processing efficiently. |
| **Maintainability** | Layered design isolates logic and UI changes. |

### **4.5 Technology Stack**

| **Component** | **Technology Used** |
|----------------|--------------------|
| **Frontend / Dashboard** | React.js / Figma for UI design |
| **Backend Server** | Python (Flask / FastAPI) |
| **Processing Modules** | Python, OpenCV, PDAL, TensorFlow |
| **Database** | PostgreSQL / MongoDB with PostGIS |
| **Visualization** | Plotly, Dash, Leaflet.js |
| **Deployment** | Docker, AWS Cloud |

---

## **5. Non-Functional Requirements**

| **Category** | **Requirement** |
|---------------|----------------|
| **Performance** | System must process large PCD datasets (≥ 1 GB) efficiently. |
| **Scalability** | Must support integration of additional sensors or models. |
| **Usability** | Dashboard must be simple, responsive, and intuitive. |
| **Reliability** | Data loss prevention and backup mechanisms required. |
| **Security** | All user data must be encrypted and securely accessed. |
| **Maintainability** | Codebase must follow modular and documented structure. |

---

## **6. Database Design**

### **6.1 Main Entities**
- **Tree:** Individual tree data with height, diameter, coordinates.  
- **Plot:** Spatial grouping of trees.  
- **BiomassRecord:** Computed biomass data linked to tree/plot.  
- **Metadata Index:** Manages versioning, upload dates, and source type.  

---

## **7. Constraints**
- Requires consistent and accurate aerial imagery input.  
- High computation time for large areas.  
- Internet access required for dashboard and database connectivity.  

---

## **8. Future Enhancements**
- Integration with real-time satellite monitoring.  
- Machine learning-based species classification.  
- Cloud-based collaborative analytics platform.  

---

## **9. Conclusion**
The **Forest Biomass Estimation and Monitoring System** provides an end-to-end solution for environmental data analysis and visualization.  
Its layered architecture ensures modular development, scalability, and maintainability while meeting research and operational needs for sustainable forest management.
