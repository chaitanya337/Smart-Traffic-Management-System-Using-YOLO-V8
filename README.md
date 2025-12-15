# Smart Traffic Management System Using YOLOv8


Project Overview
----------------
Smart Traffic Management System is a Python-based AI application that uses YOLOv8 for real-time vehicle detection and SORT algorithm for automated tracking and density calculation. The system dynamically adjusts traffic signal timings based on real-time traffic conditions and provides automatic priority for emergency vehicles (ambulances, fire trucks, police cars).

Features
--------
- Real-time vehicle detection using YOLOv8 (cars, buses, trucks, bikes, autos, emergency vehicles)
- Vehicle tracking with SORT algorithm to prevent double counting
- Adaptive green-time control based on traffic density
- Emergency vehicle priority system with instant lane switching
- Interactive simulation dashboard with Pygame
- Lane-wise density calculation and traffic flow monitoring
- Visual lane labels (lane 1, lane 2, lane 3, lane 4) on simulation


Installation
------------
Prerequisites
- Python 3.8 or higher
- pip package manager
- Git

Setup Steps
-----------
1. Clone the repository:

	git clone https://github.com/chaitanya337/Smart-Traffic-Management.git
	cd Smart-Traffic-Management

2. Create and activate a virtual environment (recommended)

	Linux / macOS:

	python3 -m venv traffic_env
	source traffic_env/bin/activate

	Windows (PowerShell):

	python -m venv traffic_env
	.\traffic_env\Scripts\Activate.ps1

	Windows (cmd.exe):

	python -m venv traffic_env
	traffic_env\Scripts\activate.bat

3. Install dependencies:

	pip install -r requirements.txt

4. Model Training :

	A custom dataset was created and trained using Ultralytics YOLOv8 in Kaggle Notebook.
	The trained model is already integrated into the project.
	
	If you want to retrain the model:
	- Create your own dataset with traffic images and with it lables 
	- Upload to Kaggle and use Ultralytics YOLOv8 for training
	- Replace the model file in the project directory

5. Run the simulation:

	python simulation.py

6. Open the Pygame window to view the traffic intersection simulation.


Usage
-----
The simulation displays a four-lane traffic intersection with adaptive signal control. Vehicles are automatically generated and move through lanes based on traffic signal states.

- Lane labels (lane 1, lane 2, lane 3, lane 4) are displayed on the greenery areas
- Traffic signals dynamically adjust green-time based on vehicle density
- Emergency vehicles trigger instant priority and lane switching
- Vehicle counts and signal timings are displayed in real-time


System Architecture
-------------------
The system operates in three layers:

A. Sensing Layer
- CCTV / IP Camera captures real-time video feed
- Edge device / PC receives frames

B. Processing & Intelligence Layer
- YOLOv8 model detects vehicles per frame
- SORT assigns unique IDs and tracks motion
- Tripwire logic counts vehicles crossing intersection
- ASCL (Adaptive Signal Control Logic) calculates green time
- Emergency detection overrides control flow for priority passage

C. Control & Actuation Layer
- Traffic light controller updates signals
- GUI dashboard displays live detections, counts, and timings
- Real-time statistics displayed on screen


Technologies Used
-----------------
- Python (Primary development language)
- YOLOv8 (Ultralytics) - Real-time object detection
- SORT Algorithm - Vehicle tracking
- OpenCV - Frame processing
- Pygame - Traffic light animation & simulation
- NumPy & Pandas - Data handling


Implementation Flow
-------------------
0. Dataset Creation & Model Training (Done in Kaggle Notebook):
   - Created custom traffic dataset with vehicle images
   - Trained YOLOv8 model using Ultralytics on Kaggle
   - Fine-tuned model for traffic-specific vehicle detection

1. Import libraries & load trained YOLOv8 model
2. Capture live or offline video stream
3. Detect vehicles frame-by-frame using custom-trained YOLOv8
4. Track each vehicle using SORT
5. Count vehicles and compute density per lane
6. Apply ASCL to compute green signal duration
7. Trigger emergency priority if needed
8. Update GUI and signal controller
9. Display real-time statistics on simulation


Results Summary
---------------
- Custom dataset created and trained using Ultralytics YOLOv8 in Kaggle Notebook
- YOLOv8 achieved >90% accuracy in detecting cars and emergency vehicles
- Successfully simulated real-time traffic with adaptive signals
- Emergency detection triggered instant priority in simulations
- Reduced average waiting time by 30-40% compared to fixed-time signals

Model Evaluation Metrics:
- F1 Confidence Curve
- Precision–Recall Curve
- Precision Confidence Curve
- Recall Confidence Curve


Key Features
------------
- Real-Time Vehicle Detection: YOLOv8 detects vehicles with >90% accuracy
- Vehicle Counting via SORT: Unique ID tracking prevents double counting
- Adaptive Green-Time Control: More vehicles → longer green time, Less traffic → shorter green time
- Emergency Vehicle Priority: Instant green signal for ambulance/fire engine/police car
- Simulation Dashboard: Displays lane density, active signal, emergency alerts, and lane labels
- Console Statistics: Vehicle counts and signal timings printed to console


Project Structure
-----------------
Smart-Traffic-Management/
├── simulation.py              # Main simulation file
├── images/                    # Vehicle and signal images
│   ├── down/                  # Vehicles moving down
│   ├── left/                  # Vehicles moving left
│   ├── right/                 # Vehicles moving right
│   ├── up/                    # Vehicles moving up
│   └── signals/               # Traffic signal images
├── traffic_env/               # Virtual environment
├── README.md                  # Project documentation
├── requirements.txt           # Python dependencies
└── .gitignore                 # Git ignore file



Contact
-------
Name: Chaitanya Vardhineedi

Email: chaitanyavardhineedi@gmail.com

GitHub: @chaitanya337
