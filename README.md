Predictive Maintenance: Turbofan Engine RUL Estimation

    Achieved an RMSE of 18.8 on the NASA CMAPSS FD001 dataset using specialized feature engineering and RUL clipping.

✈️ Project Overview

This project develops a predictive maintenance pipeline to estimate the Remaining Useful Life (RUL) of aircraft engines. By analyzing telemetry data from 21 sensors (temperatures, pressures, fan speeds), the model identifies degradation patterns before they lead to catastrophic failure.
🛠️ Technical Approach

This implementation goes beyond basic regression by applying domain-specific data constraints:

    Asymptotic RUL Clipping (115 Cycles): To account for the "initial healthy period" of an engine, the target RUL was capped at 115. This prevents the model from trying to learn degradation patterns in engines that are still operating at peak performance.

    Sensor Filtering: Reduced dimensionality and noise by removing zero-variance sensors (s1, s5, s10, s16, s18, and s19) that do not contribute to the degradation signal.

    Temporal Feature Engineering: Implemented rolling window statistics to capture the trajectory of sensor values, which is a more stable indicator of wear than raw point-in-time snapshots.

📊 Dataset

The project utilizes the NASA CMAPSS (Commercial Modular Aero-Propulsion System Simulation) dataset.

    Condition: Sea level.

    Fault Mode: High-Pressure Compressor (HPC) degradation.

    Units: 100 engines for training, 100 for testing.

🚀 Model Performance

    Algorithm: [HistGradientBoostingRegressor]

    Metrics: 
    Model Accuracy on Unseen Engines:
    Mean Absolute Error: 13.84 cycles
    Root Mean Squared Error: 18.87 cycles
    R^2 Score: 0.7939


Observation: The model shows high precision in the final 30 cycles of engine life, which is the most critical window for maintenance scheduling.
