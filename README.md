# Zero-shot Indoor Navigation using 2D Semantic Map and Agentic Task Planning

## Project Overview

This project implements an autonomous navigation system for a mobile robot that can navigate through an environment using A\* path planning and semantic map inference. It combines computer vision, natural language processing, and robot control to create a system that can understand semantic descriptions of locations and plan paths to reach them.

## Features

- **A\* Path Planning**: Efficient path planning algorithm that accounts for obstacles and clearance
- **Semantic Map Inference**: Uses CLIP and LSeg models to understand natural language location descriptions
- **UDP Communication**: Reliable communication protocol for sending trajectories to the robot
- **Visualization Tools**: Various utilities for visualizing maps, paths, and robot positions

## System Components

1. **Robot Controller**: Manages the high-level navigation tasks
2. **A\* Path Planner**: Plans optimal paths through the environment
3. **Map Inference Server**: Processes semantic queries about locations
4. **UDP Communication**: Handles communication with the physical robot
5. **Visualization Tools**: For debugging and monitoring

## Requirements

```bash
# Core dependencies
pip install -r requirements.txt
```

Key dependencies:

- PyTorch with CUDA support (recommended)
- CLIP by OpenAI
- OpenCV
- Flask (for the inference server)
- NumPy, Matplotlib
- Additional tools for 3D visualization and map processing

## Getting Started

### 1. Setup

1. Clone this repository:

```bash
git clone https://github.com/yourusername/6500-final-project.git
cd 6500-final-project
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Prepare map files:
   - Place your map PGM file in the `maps/` directory
   - Update the corresponding YAML file with map parameters

### 2. Running the System

1. Start the map inference server:

```bash
python map_inference_server.py
```

2. Generate goal points using the agent:

```bash
python agent.py
```

This will generate the navigation goals based on semantic queries and save them for the navigation system.

3. Run the main navigation program to send commands to the car:

```bash
python main.py
```

The main program will use the generated goal points and send appropriate commands to the car for autonomous navigation.

## Map Configuration

The system uses occupancy grid maps (PGM format) with corresponding YAML configuration files that define:

- Resolution (meters/pixel)
- Origin coordinates
- Occupied/free space thresholds

## Tools

The `tools/` directory contains several utilities:

- `combine_pose_files.py`: Merges multiple pose data files
- `create_map.py`: Generates maps from sensor data
- `mcap_extract.py`: Extracts data from MCAP format
- `viz_3d_map.py`: 3D visualization of maps
- `viz_all_poses.py`: Visualizes robot poses

## LSeg Integration

The project integrates LSeg (Language-driven Semantic Segmentation) for semantic understanding of the environment. The LSeg model is used to create feature embeddings of the map that can be queried using natural language.

## UDP Communication Protocol

The UDP communication module (`udp_comm.py`) handles sending trajectory waypoints to the robot. The protocol includes:

- Start and end markers for reliable transmission
- CSV-based trajectory format
- Position feedback mechanisms

## License

[Add your license information here]

## Contributors

[Add contributor information here]

## Acknowledgements

This project was developed as part of the 6500 course.
