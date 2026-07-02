# OCW Project - Road Degradation Analysis Tool

A Python application that calculates road degradation over time and provides an interactive visualization dashboard. Built with geospatial analysis tools for analyzing road component conditions and maintenance scenarios.

## Features

- **Road Degradation Analysis**: Calculate how road conditions degrade over specified time periods
- **Interactive Dashboard**: View analysis results in a beautiful web-based interface (Panel)
- **Scenario Management**: Create and compare different maintenance scenarios
- **Geospatial Visualization**: Map-based views with Folium and Bokeh
- **Cross-Platform Support**: Run natively or with Docker for complete OS independence

## Requirements

- **Python 3.12** or higher
- **Git** (for cloning the repository)

### System Dependencies

The project uses geospatial packages (GeoPandas, GEOS, PROJ) that require system libraries:

**Windows Users**: These dependencies are automatically handled if you use Docker (recommended).

**macOS/Linux**: System dependencies are included in the Docker setup.

## Installation & Setup

### Option 1: Docker (Recommended - Works on All Platforms)

Docker ensures all system dependencies are correctly installed, regardless of your OS.

1. **Install Docker**
   - Download from: https://www.docker.com/products/docker-desktop
   - Choose the Windows version and install

2. **Clone the repository**
   ```bash
   git clone https://github.com/Joewi44/ocw_project.git
   cd ocw_project_repo
   ```

3. **Build the Docker image**
   ```bash
   docker build -t ocw-app ./ocw_project
   ```

4. **Run the application**
   ```bash
   docker run -p 5006:5006 ocw-app
   ```

5. **Access the dashboard**
   - Open your browser to: `http://localhost:5006/frontend_app`

### Option 2: Native Python Installation (macOS/Linux)

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd python_projects
   ```

2. **Create a virtual environment**
   ```bash
   python3.12 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r ocw_project/requirements.txt
   ```

4. **Install the package**
   ```bash
   pip install -e ocw_project/
   ```

5. **Run the application**
   ```bash
   python ocw_project/ocw_project/cli.py
   ```

6. **Access the dashboard**
   - The application will automatically open in your browser at: `http://localhost:5006/frontend_app`

## Quick Start

### Using Docker (All Platforms - Windows Recommended)
```bash
# Build image
docker build -t ocw-app ./ocw_project

# Run application
docker run -p 5006:5006 ocw-app

# Access at http://localhost:5006/frontend_app
```

### Using Python Directly
```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install and run
pip install -r ocw_project/requirements.txt
pip install -e ocw_project/
python ocw_project/ocw_project/cli.py
```

## Project Structure

```
ocw_project/
├── ocw_project/
│   ├── cli.py                 # Entry point for the application
│   ├── OcwSystematiek.py      # Core degradation calculation logic
│   ├── WegVakonderdeel.py     # Road component models
│   ├── config/                # Configuration files (scenarios, simulation, etc.)
│   └── viewer/                # Web dashboard and frontend
├── requirements.txt           # Python dependencies
├── setup.py                   # Package setup configuration
├── Dockerfile                 # Docker configuration
└── tests/                     # Test files
```

## Troubleshooting

### Windows Users

**Issue**: Port 5006 already in use
- Windows tends to reserve ports. Try a different port by modifying the Docker command:
  ```bash
  docker run -p 5007:5006 ocw-app
  ```
  Then access at `http://localhost:5007/frontend_app`

**Issue**: Docker not starting
- Make sure Docker Desktop is running before executing commands
- Check that virtualization is enabled in your BIOS

### All Platforms

**Issue**: Cannot connect to localhost:5006
- Verify the application is running (check console output)
- Ensure no firewall is blocking the connection
- Wait 5-10 seconds after starting - the application needs time to initialize

**Issue**: Dependencies installation fails
- With Docker: This shouldn't happen - Docker handles all system dependencies
- With Python: Use Docker instead (recommended) as geospatial packages have complex system requirements

## Development

To set up a development environment:

```bash
# Clone and create virtual environment
git clone <repository-url>
cd python_projects
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install in editable mode with dev dependencies
pip install -e ocw_project/

# Run tests
python -m pytest ocw_project/tests/
```

## Technology Stack

- **Panel**: Web dashboard framework (Bokeh-based)
- **GeoPandas**: Geospatial data analysis
- **Folium & HVPlot**: Interactive mapping and visualization
- **Pandas**: Data manipulation
- **Bokeh**: Interactive visualizations

## Port Information

The application runs on **port 5006** by default. This can be modified in [ocw_project/cli.py](ocw_project/cli.py) if needed.

## Notes for Contributors

- Python 3.12+ required
- All geospatial dependencies are system-level and best managed via Docker
- Dashboard auto-reloads on file changes when running natively (but not in Docker)
- The application uses Panel's websocket connection, so network/firewall may need adjustment in corporate environments

## License

[Add your license here]

## Contact

Created by Uwe Versavel (Uwe.versavel@telenet.be)

---

**Recommended for Windows users**: Use Docker for a hassle-free setup without dealing with complex system dependencies.