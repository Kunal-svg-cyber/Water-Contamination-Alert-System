Intelligent Municipal Water Contamination & Infrastructure Alert System

SDG 6 — Clean Water and Sanitation

An AI-powered system that predicts water contamination and pipeline anomalies from simulated IoT sensor data, then automatically triggers an emergency response pipeline — shutdown signal, maintenance ticket, and citizen/authority alert.

Problem

Water treatment plants and city pipelines often detect chemical spikes or leakages too late, leading to public health crises and wasted water. Manual monitoring can't keep up with the volume and speed of sensor data from a modern water network.

Solution

This project simulates a network of IoT water sensors (pH, turbidity, dissolved oxygen, flow rate) across multiple pipeline nodes, trains a machine learning model to detect contamination and leak anomalies in real time, and automates the emergency response workflow end-to-end.

How It Works


Data — Sensor readings are derived from a real water quality dataset (Kaggle), extended with synthetic node IDs, GPS coordinates, timestamps, dissolved oxygen, and flow rate to simulate a live multi-node sensor network.
Prediction — A Random Forest classifier flags each new reading as none, contamination, or leak based on the four sensor values.
Automation — When an anomaly is detected, the pipeline automatically:

Sends an emergency shutdown signal for that pipeline node
Generates a maintenance ticket with GPS coordinates and the exact reading that triggered it
Dispatches an alert (email/SMS) to affected citizens and local authorities



Dashboard — A Streamlit app visualizes node status on a map, live sensor trends, open maintenance tickets, and recent automated actions.


Tech Stack

All free and open-source:

ComponentToolDataKaggle water quality dataset + synthetic augmentationMLscikit-learn (Random Forest)Data handlingpandas, numpyDashboardStreamlitAlertsPython smtplib (Gmail SMTP)Notebook environmentGoogle Colab

Project Structure

├── water_alert_system.ipynb   # Colab notebook: data prep, model training, pipeline simulation
├── app.py                     # Streamlit dashboard
├── requirements.txt           # Python dependencies
├── water_sensor_data.csv      # Generated sensor dataset
├── water_anomaly_model.pkl    # Trained Random Forest model
├── pipeline_log.csv           # Log of automated pipeline actions
├── shutdown_log.csv           # Log of simulated shutdown signals
└── ticket_*.json              # Auto-generated maintenance tickets

Running Locally


Clone this repository
Install dependencies:


bash   pip install -r requirements.txt


Run the dashboard:


bash   python -m streamlit run app.py


Open http://localhost:8501 in your browser


Generating the Data & Model

The dataset, model, and logs are produced by water_alert_system.ipynb. Open it in Google Colab, run all cells in order, and download the generated files into this project folder before running the dashboard.

Limitations


Sensor data is simulated/augmented, not from real physical hardware
Model performance depends on the quality and balance of the underlying dataset
Alerts and shutdown signals are simulated for demonstration; no real infrastructure or SMS/email credentials are included in this repository


Future Work


Integrate real IoT sensor hardware and live data streams
Add time-series forecasting to predict anomalies before they occur, not just detect them
Expand alerting to real SMS via Twilio and push notifications
Add authentication and role-based access for water authority staff


License

This project was built for educational purposes as part of an SDG 6 initiative.
