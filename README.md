## Neurofeedback Learning Platform
An EEG-powered adaptive learning engine that enhances study outcomes by personalizing content in real time based on brain activity.

### Project Overview
The Neurofeedback Learning Platform is a Streamlit-based application that processes EEG (electroencephalogram) signals and translates them into actionable insights about a learner’s cognitive state. It supports both offline analysis (uploading EEG files in .mat or .edf formats) and real-time monitoring. By classifying mental states such as Focused, Distracted, Fatigued, Stressed, or Other, the tool adapts study material dynamically to improve learning efficiency and engagement.

The tool is deployed as a standalone Streamlit app, and it is also embedded within a broader website that provides additional information:

[Neurofeedback Ai Learning Platform](https://neurofeedback-ai.lovable.app/tool)

### Key Features
Offline Mode: Upload EEG files for batch analysis and prediction.

Real-Time Mode: Stream live EEG signals for continuous monitoring.

Signal Preprocessing: Bandpass filtering, segmentation, normalization.

Feature Extraction: Bandpower, Hjorth parameters, spectral entropy.

State Classification: Random Forest baseline, CNN, LSTM, CNN+BiLSTM hybrid models.

Adaptive Learning Engine: Maps predicted states to study actions.

Deployment: Streamlit interface for usability and demonstration.

### Tool Interface
Below is a screenshot of the EEG Live Prediction Tool interface, showing the Offline Mode where users can upload EEG files (MAT, EDF) for analysis:

<img width="1083" height="367" alt="image" src="https://github.com/user-attachments/assets/ee550a79-f553-430f-b148-c017a0f1a897" />


### Installation
```bash
git clone https://github.com/yourusername/neurofeedback-ai.git
cd neurofeedback-ai
pip install -r requirements.txt
streamlit run app/app.py
Access the app locally:
```
Code
```http://localhost:8501```
Project Structure
```Code
├── data/                # EEG datasets (.mat, .edf)
├── preprocessing/        # Filtering, segmentation, normalization
├── features/             # Bandpower, Hjorth, entropy extraction
├── models/               # RandomForest, CNN, LSTM, CNN+BiLSTM
├── evaluation/           # Reports, confusion matrices, error analysis
├── adaptive_engine/      # Real-time neurofeedback actions
├── app/                  # Streamlit app scripts
└── saved_models/         # Trained models (.h5) and encoders (.pkl)
```
Quick Start Example
```python
from preprocessing import bandpass_filter, segment_signal
from features import extract_features
from adaptive_engine import adaptive_engine
import mne, joblib, tensorflow as tf

raw = mne.io.read_raw_edf("sample.edf", preload=True)
ch, sf = raw.get_data()[0], int(raw.info['sfreq'])

epochs = segment_signal(bandpass_filter(ch, sf), sf)
features = extract_features(epochs[0], sf)

model = tf.keras.models.load_model("saved_models/cnn_lstm_model.h5")
encoder = joblib.load("saved_models/label_encoder.pkl")
print(adaptive_engine(model, encoder, ch, sf=sf)[:5])
```
### Contribution Guidelines
i. Fork the repository.

ii. Create a feature branch (git checkout -b feature-name).

iii. Commit changes (git commit -m "Add new feature").

iv. Push to branch (git push origin feature-name).

v. Open a Pull Request.

Standards:

- Code must be modular and well-documented.

- Visualizations should be clear and reproducible.

- Contributions should include evaluation results.


### Impact
This project demonstrates:

- Technical depth in EEG signal processing and deep learning.

- Practical application of AI in adaptive learning.

- A recruiter-ready portfolio piece with a deployed Streamlit app, showing end-to-end workflow and real-world relevance.
