# Interoperability Center (ICP Map) Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Java](https://img.shields.io/badge/Java-21-orange.svg)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-green.svg)](https://spring.io/projects/spring-boot)
[![React](https://img.shields.io/badge/React-19-blue.svg)](https://react.dev/)
[![MySQL](https://img.shields.io/badge/MySQL-8.0-blue.svg)](https://www.mysql.com/)

An open, high-performance Smart City and IoT Interoperability Platform designed for municipal infrastructure monitoring, geospatial visualization, and predictive analytics. Developed for the Municipality of Patras, Greece.

---

## About the Project

The Interoperability Center (ICP Map) aggregates heterogeneous urban IoT streams—such as smart waste bins, parking availability sensors, environmental monitors, pedestrian traffic gates, and municipal infrastructure assets—into a unified geospatial control dashboard.

By combining real-time spatial clustering, time-series telemetry analysis, and machine learning load forecasting, the platform enables city operators to monitor asset status, streamline maintenance workflows, and make data-driven urban management decisions.

---

## Core Features

* **Real-time GIS Visualization**: Dynamic interactive map rendering with high-performance point clustering for thousands of IoT assets.
* **Unified Asset Management**: Monitored asset categories include Smart Bins, Parking Sensors, Environmental Sensors, LoRaWAN Gateways, Bollards, Fiber Cabinets, Smart Crossings, Smart Bus Stops, and Variable Message Signs.
* **Historical Telemetry Analysis**: Built-in SVG chart engine visualizing time-series trend data across customizable historical ranges.
* **Operational Log Ledger**: Centralized logging system allowing field operators to submit status updates, record notes, and manage operational logs with single-click removal.
* **Predictive Analytics**: Integrated Python Machine Learning service for load forecasting and request modeling.
* **Automated Spatial Boundary Mapping**: MySQL spatial geometry functions matching asset lat/lng coordinates to administrative municipal boundaries.

---

## Platform Architecture

The system uses a microservices architecture composed of two main components:

1. **Frontend Dashboard (`interoperability-center-frontend`)**: Web user interface built with React 19, Vite, and Leaflet GIS.
2. **Server & Engine (`interoperability-center-server`)**: REST API powered by Spring Boot (Java 21), a Python ML analytics microservice, and a MySQL 8.0 GIS spatial database.

---

## Technology Stack

### Client Side
* **Framework**: React 19, Vite
* **Mapping & GIS**: Leaflet, React-Leaflet, Supercluster
* **UI Components**: Lucide React, FontAwesome

### Server Side
* **Core API Service**: Java 21, Spring Boot 3, Spring Data JPA / Hibernate
* **Database**: MySQL 8.0 (Spatial Extensions)
* **Analytics Engine**: Python 3.10, Flask, Scikit-learn
* **Containerization**: Docker, Docker Compose

---

## Getting Started

### Prerequisites
* [Docker](https://www.docker.com/) and [Docker Compose](https://docs.docker.com/compose/)
---

### Installation & Deployment

#### 1. Clone the Repositories
```bash
git clone https://github.com/your-org/interoperability-center-server.git
git clone https://github.com/your-org/interoperability-center-frontend.git
```

#### 2. Start the Backend Ecosystem
```bash
cd interoperability-center-server
docker-compose up -d --build
```
* **Database**: `localhost:3306`
* **REST API**: `http://localhost:5000`
* **ML Service**: `http://localhost:5001`

#### 3. Start the Frontend Application
```bash
docker-compose up -d --build
```
* **Web UI**: Access the application at `http://localhost:5173`

---

## API Overview

The REST API exposes standardized endpoints for retrieving asset locations, updating operational statuses, managing log notes, and querying telemetry history:

* `GET /api/sensors` - Retrieve standard sensor entities
* `GET /api/bins` - Retrieve smart waste collection bins
* `GET /api/parking-sensors` - Retrieve real-time parking availability sensors
* `GET /api/{category}/{id}/history` - Fetch time-series telemetry history
* `POST /api/{category}/{id}/status` - Submit status updates and operational notes
* `DELETE /api/{category}/{id}/logs/{logId}` - Remove operational log entries

---

## License

Distributed under the MIT License. See `LICENSE` for more information.
