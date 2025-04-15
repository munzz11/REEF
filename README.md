# REEF (Robotic Environment Exploration Framework)

[![GitHub issues](https://img.shields.io/github/issues/munzz11/reef)](https://github.com/munzz11/reef/issues)

REEF is a comprehensive platform for managing and visualizing post op mission data. This tool is built and configured for use in the UNH CCOM ASV Lab

## Components

### Data Gateway 
[![Docker Pulls](https://img.shields.io/docker/pulls/munzz11/reef-data-gateway)](https://hub.docker.com/r/munzz11/reef-data-gateway)
[![Docker Image Size (latest by date)](https://img.shields.io/docker/image-size/munzz11/reef-data-gateway)](https://hub.docker.com/r/munzz11/reef-data-gateway)
- Handles data ingestion from robotic platforms
- Validates and processes incoming data
- Stores data in MongoDB
- [View Documentation](services/data-gateway/README.md)

### Map Dashboard
[![Docker Pulls](https://img.shields.io/docker/pulls/munzz11/reef-map-dashboard)](https://hub.docker.com/r/munzz11/reef-map-dashboard)
[![Docker Image Size](https://img.shields.io/docker/image-size/munzz11/reef-map-dashboard/latest)](https://hub.docker.com/r/munzz11/reef-map-dashboard)

- Interactive web-based map viz tool
- Real-time and historical data display
- Deployment and platform filtering
- KML export functionality
- [View Documentation](web/map-dashboard/README.md)

## Quick Start

### Prerequisites
- Docker and Docker Compose
- Go 1.21+ (for development)
- Python 3.11+ (for development)

### Running with Docker Compose
1. Clone the repository:
```bash
git clone https://github.com/munzz11/reef.git
cd reef
```

2. Start the services:
```bash
docker-compose -f deployment/compose/docker-compose.yml up
```

3. Access the dashboard:
- Map Dashboard: http://localhost:5001

## Development

### Local Development Setup
1. Start the data gateway:
```bash
cd services/data-gateway
go run main.go
```

2. Start the map dashboard:
```bash
cd web/map-dashboard
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python app.py
```

## Project Structure
```
reef/
├── services/
│   └── data-gateway/     # Data ingestion and processing service
├── web/
│   └── map-dashboard/    # Web-based visualization dashboard
└── deployment/
    └── compose/          # Docker Compose configurations
```

## Environment Variables

### Data Gateway
| Variable | Description | Default |
|----------|-------------|---------|
| API_HOST | HTTP server host | 0.0.0.0 |
| API_PORT | HTTP server port | 8080 |
| MONGODB_URI | MongoDB connection string | mongodb://mongodb:27017 |
| MONGODB_DATABASE | Database name | robotics |
| MONGODB_COLLECTION | Collection name | robot_data |


### Map Dashboard
| Variable | Description | Default |
|----------|-------------|---------|
| API_URL | Data Gateway API URL | http://data-gateway:8080 |
| FLASK_RUN_HOST | Flask server host | 0.0.0.0 |
| FLASK_RUN_PORT | Flask server port | 5001 |
