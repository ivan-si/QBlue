# QBlue: NYUAD 2025
<p align="center">
<img width="306" alt="Screenshot 2025-04-27 at 3 27 26 PM" src="https://github.com/user-attachments/assets/d27afc8e-e195-4ca8-8545-3a0129eb819b" />
</p>
# QBlue: NYUAD 2025



**A Quantum Sensing & Quantum Machine Learning solution harnessing blue energy at oceanic confluences, by predicting ideal flow rates with sustainable gradients for clean energy.**

## Problem Statement

Blue Energy, derived from the salinity gradient between freshwater and saltwater, represents a vast and largely untapped renewable energy source. The most potent locations for harnessing blue energy are where rivers meet the ocean, with an estimated 1300 such confluences globally. Our goal is to optimize non-invasive blue energy plants by leveraging quantum sensing and quantum recurrent neural networks (QRNNs). This approach aims to maximize power production by dynamically predicting optimal operational parameters based on real-time environmental conditions in both fresh and saltwater sources.

---

## Solution Overview

QBlue proposes a novel system that integrates:

1.  **Simulated Environmental Data:** Generation of realistic time-series data for parameters like temperature, pressure, and salinity for both fresh and saline water sources. This is crucial for training our predictive models.
2.  **Quantum Recurrent Neural Networks (QRNNs):** A QRNN model, primarily developed in `QNN.ipynb` and further explored with Qiskit integration in `QNNqbraid.ipynb`, is trained on this simulated data. The model is designed to learn complex temporal dependencies and predict:
    * Optimal flow rates required to maximize energy efficiency under given environmental conditions.
    * The potential energy output of a conventional system versus a system optimized using Quantum Machine Learning (QML).
3.  **Energy Analytics Dashboard:** A web-based dashboard, built using React (`EnergyDashboard.jsx`), visualizes the predicted energy outputs and the underlying simulated sensor data. This provides a clear, interactive comparison between standard operational outputs and those achievable with quantum-optimization strategies.

This project aims to demonstrate the potential of quantum machine learning to significantly enhance the efficiency and economic viability of blue energy technologies, paving the way for cleaner and more sustainable energy generation.

---

## Features

* **Quantum-Enhanced Energy Prediction:** Employs a QRNN to forecast optimal operating conditions for blue energy generation, adapting to changing environmental inputs.
* **Simulated Sensor Data Generation:**
    * The `QNN.ipynb` notebook generates normalized physical data (flow, temperature, concentration) and defines an efficiency function (`raw_eff`) to derive optimal flow targets.
    * The `EnergyDashboard.jsx` React component generates 24-hour datasets for fresh and saline water temperature, pressure, and salinity using sinusoidal patterns with added noise, mimicking real-world sensor inputs for visualization.
* **Comparative Analytics:** The dashboard offers a side-by-side comparison of "Regular Output" and "QML Optimized" energy generation, highlighting the benefits of the quantum approach.
* **Interactive Data Visualization:** Utilizes `Recharts` library in the React dashboard to display:
    * Energy output over time (Regular vs. QML).
    * Hourly trends for temperature, pressure, and salinity for both fresh and saline water inputs.
* **Modular QML Model:** The QRNN is built with PennyLane and PyTorch, allowing for flexibility in quantum circuit design and training.
* **Exploratory Qiskit Integration:** `QNNqbraid.ipynb` explores the use of Qiskit for running parts of the QRNN on remote quantum backends (e.g., IBM's `ibm_brisbane`), though this is currently in an experimental phase.
* **Modern Web Interface:** A sleek, responsive, dark-themed dashboard built with React and styled with Tailwind CSS for an intuitive user experience.

---

##  Technical Stack

* **Quantum Machine Learning (Backend & Model Development):**
    * **Languages:** Python
    * **Core Libraries:**
        * [PennyLane](https://pennylane.ai/): For differentiable quantum programming and QML model construction.
        * [PyTorch](https://pytorch.org/): As the machine learning framework for defining and training the QRNN, integrating seamlessly with PennyLane's `TorchLayer`.
        * [NumPy](https://numpy.org/): For numerical operations and data manipulation.
    * **Quantum Simulation/Execution (Exploratory):**
        * [Qiskit](https://qiskit.org/): Used in `QNNqbraid.ipynb` for exploring integration with IBM quantum backends.
    * **Data Visualization (Notebooks):** Matplotlib
    * **Development Environment:** Jupyter Notebooks (`.ipynb`)

* **Frontend (Energy Analytics Dashboard):**
    * **Framework:** [React.js](https://reactjs.org/) (using functional components and hooks)
    * **Charting Library:** [Recharts](https://recharts.org/): For creating interactive and responsive charts.
    * **Styling:** [Tailwind CSS](https://tailwindcss.com/), Custom CSS (`App.css`, `index.css`).
    * **Core Language:** JavaScript (JSX)

---

## Project Structure


* QNN.ipynb               # Main Jupyter Notebook: QRNN model development, data simulation, training, and evaluation.
* QNNqbraid.ipynb         # Exploratory Jupyter Notebook: QRNN with Qiskit for remote backend execution.
* README.md               # This README file.
* index.html          # Main HTML page for the React app.
* App.css             # General styles for the React application.
* App.js              # Main React application component, renders EnergyDashboard.
* App.test.js         # Basic tests for the App component (default Create React App test).
* EnergyDashboard.jsx # React component for the energy analytics dashboard UI, data simulation, and chart rendering.
* index.css           # Global CSS styles.
* index.js            # Entry point for the React application, renders the App component.
* logo.svg            # Application logo (as imported in App.js, default from Create React App).
* reportWebVitals.js  # React performance reporting utility.

---

## Getting Started

### Prerequisites

* **For Quantum Machine Learning (Jupyter Notebooks):**
    * Python (3.8+ recommended)
    * Jupyter Notebook or JupyterLab
    * Installation of required Python packages:
        ```bash
        pip install torch pennylane matplotlib numpy qiskit pandas
        ```
        *(`qiskit` and `pandas` are primarily for `QNNqbraid.ipynb` and data handling within notebooks.)*

* **For Frontend (React Dashboard):**
    * Node.js (v14+ recommended)
    * npm (comes with Node.js) or yarn

### Running the Frontend Dashboard

1.  **Clone the repository (if applicable) and navigate to the project root directory** (where `package.json` for the React app would be located, typically the root or a `frontend/` subfolder).
2.  **Install dependencies:**
    ```bash
    npm install
    ```
    or
    ```bash
    yarn install
    ```
3.  **Start the development server:**
    ```bash
    npm start
    ```
    or
    ```bash
    yarn start
    ```
    This will usually open the dashboard in your default web browser, typically at `http://localhost:3000`.

### Running the QML Models (Jupyter Notebooks)

1.  **Ensure all Python prerequisites listed above are installed.**
2.  **Start Jupyter Notebook or JupyterLab from your terminal:**
    ```bash
    jupyter notebook
    ```
    or
    ```bash
    jupyter lab
    ```
3.  **Navigate to and open `QNN.ipynb` or `QNNqbraid.ipynb`** in the Jupyter interface.
4.  **Run the cells sequentially** to execute the data generation, model definition, training, and visualization steps.

---

## 🔬 Code Highlights

### `EnergyDashboard.jsx` (Frontend)

This React component is the heart of the visual analytics interface.
* **Simulated Data Generation (`generateData` function):** Creates 24-hour time-series data for fresh and saline water parameters (temperature, pressure, salinity) using sinusoidal functions with added random noise to simulate realistic fluctuations.
* **Energy Output Calculation:**
    * `regularOutput`: Calculated based on a heuristic formula involving pressure differences, salinity differences, and a temperature factor between the fresh and saline sources.
    * `qmlOutput`: Simulates the enhanced energy output achievable with QML optimization by applying an improvement factor (e.g., 2% base improvement + closing 40% of the gap to a theoretical maximum) over the `regularOutput`.
* **State Management:** Uses the `useState` hook for managing UI elements like the displayed `currentMonth` (though full date navigation logic might be more extensive).
* **Chart Rendering with Recharts:** Dynamically renders:
    * A main "Energy Output Comparison" line chart (Regular vs. QML).
    * Six smaller line charts for individual parameters: Fresh Temperature, Saline Temperature, Fresh Pressure, Saline Pressure, Fresh Salinity, Saline Salinity.
* **Styling and Layout:** Employs Tailwind CSS utility classes for a responsive, dark-themed UI, featuring a navigation bar, a sidebar (with placeholder navigation items), and a main content area for the charts.

### `QNN.ipynb` (Core QML Model)

This notebook details the primary QRNN model for predicting optimal flow rates.
* **Parameterization:** Defines key hyperparameters for the simulation and model (batch size, sequence length, flow rate ranges, qubit numbers, learning rates, epochs).
* **Physics-Informed Data Generation:**
    * `build_phys_norm()`: Creates sequences of normalized physical parameters (flow, temperature, concentration).
    * `raw_eff()`: A function defining the energy generation efficiency based on the physical parameters.
    * `optimal_flow()`: Determines the target optimal flow rate by finding the flow that maximizes `raw_eff` for given temperature and concentration.
* **Quantum Encoding (`qubit`, `encode_to_amp`):**
    * Classical features are encoded into the amplitudes of quantum states. Each feature (normalized flow, temp, conc) is mapped to a rotation angle $\theta_i = \text{feature}_i \cdot \pi$.
    * These are combined using tensor products (Kronecker product) to form an $N_Q$-qubit state, where $N_Q = N_{IN} (\text{input features}) + N_H (\text{hidden units})$.
* **QRNN Architecture (PennyLane & PyTorch):**
    * `qrnn_cell`: A QNode representing the recurrent quantum cell. It uses `qml.AmplitudeEmbedding` for state preparation and `qml.templates.StronglyEntanglingLayers` for parameterized quantum evolution. It outputs expectation values of PauliZ operators on the hidden qubits.
    * `readout`: Another QNode that takes the final hidden state from the `qrnn_cell`, applies further rotations and entangling layers, and outputs a single expectation value (PauliZ on the first qubit) as the prediction.
    * `QRNN` class: An `nn.Module` that encapsulates the `qrnn_layer` (for the recurrent cell) and `read_layer` (for the output), processing sequences step-by-step.
* **Training and Evaluation:**
    * Trained using PyTorch's `Adam` optimizer and `MSELoss`.
    * Compares the QRNN's predictions against the `Y_true` optimal flow and evaluates performance against a simple baseline and a tiny classical MLP.
    * Visualizes results using 3D scatter plots and bar charts for efficiency and MSE.

### `QNNqbraid.ipynb` (Exploratory Qiskit Integration)

This notebook adapts the QRNN concepts for potential execution using Qiskit and IBM Quantum backends.
* **Remote Backend Configuration:** Attempts to set up PennyLane devices (`dev_rec`, `dev_out`) to use `qiskit.remote` targeting `ibm_brisbane`. *Note: The provided output indicates a `WireError`, suggesting challenges with this configuration or qubit mapping that would need debugging for successful remote execution.*
* **Quantum Encoding and QNodes:** Similar encoding and QNode structure (`qrnn_cell`, `qnn_readout`) as in `QNN.ipynb`, but adapted for the Qiskit device interface.
* **Deterministic Data:** Uses `pure_sequences` to generate noise-free input data for focused model testing.
* **Training:** Implements a training loop for the `FullyQuantumRNN` model, targeting the defined efficiency curve (`true_eff`).

---

## Future Work

* **Real Sensor Data Integration:** Transition from simulated data to real-world sensor data from actual blue energy plant locations.
* **Hardware Execution & Refinement:**
    * Resolve `WireError` and other issues in `QNNqbraid.ipynb` to enable successful execution of QRNN components on quantum hardware or advanced simulators.
    * Investigate noise mitigation and error correction techniques for hardware runs.
* **Advanced QRNN Architectures:** Explore more complex quantum circuit designs, different entangling layer configurations, and alternative quantum embedding strategies.
* **Hybrid Models:** Investigate hybrid classical-quantum models where classical neural networks handle pre-processing or post-processing tasks, while quantum layers focus on the core complex pattern recognition.
* **Dashboard Enhancements:**
    * Implement full date/month navigation and selection.
    * Add real-time data fetching capabilities (if connected to live sensors).
    * Incorporate predictive forecasting visualizations (e.g., projecting energy output for the next few hours/days).
    * User authentication and personalized settings/profiles.
* **Optimization Algorithms:** Integrate the QRNN's predictions with classical optimization algorithms to provide actionable control strategies for the blue energy plant.
* **Scalability and Deployment:** Plan for scaling the solution and deploying the dashboard and QML models in a production environment (cloud or edge).

---


  @media print {
    .ms-editor-squiggler {
        display:none !important;
    }
  }
  .ms-editor-squiggler {
    all: initial;
    display: block !important;
    height: 0px !important;
    width: 0px !important;
  }
