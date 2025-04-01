# Anomaly Detection in Linux Systems Using Behavioral Profiling of System Activities

## Project Overview
This project develops an advanced anomaly detection system for Linux environments by profiling system activities through system call sequences. The goal is to identify unusual behavior that may indicate security threats, such as intrusions, malware, or system misuse. Unlike traditional signature-based detection, this approach uses behavioral profiling to detect previously unseen anomalies, making it adaptable to evolving threats.

The system employs a **hybrid machine learning model** combining **Transformers** and **Autoencoders**. Transformers excel at modeling sequential data (e.g., system call traces), while Autoencoders learn to reconstruct normal behavior, flagging deviations as anomalies. Two models were developed and tested, with promising results on a benchmark dataset.

### Motivation
- Linux systems are widely used in servers, cloud infrastructure, and critical applications, making them prime targets for attacks.
- Traditional intrusion detection systems (IDS) struggle with zero-day attacks or subtle anomalies.
- Behavioral profiling offers a proactive, data-driven solution to enhance system security.

### Key Features
- **Behavioral Profiling**: Analyzes system call sequences to establish a baseline of normal activity.
- **Hybrid Model**: Combines Transformer’s sequential learning with Autoencoder’s anomaly detection capabilities.
- **Dataset-Driven**: Built and evaluated on the ADFA-LD dataset, a standard for Linux anomaly detection research.
- **Scalability**: Designed to handle both short and long system call sequences.

## Dataset
The project uses the **ADFA-LD (Australian Defence Force Academy - Linux Dataset)**, created by the University of New South Wales. This dataset is specifically designed for intrusion detection in Linux systems and includes:
- **Normal Data**: System call traces from common Linux processes (e.g., web servers, SSH).
- **Attack Data**: Traces from simulated attacks, such as buffer overflows, privilege escalation, and exploits.
- **Structure**: Over 800 normal traces and 10+ attack categories, with varying sequence lengths.

For more information, visit the [ADFA-LD official page](https://research.unsw.edu.au/projects/adfa-ids-datasets).

### Preprocessing
- System calls are tokenized and converted into numerical sequences.
- Sequences are padded or truncated to a fixed length for model input.
- Normal and attack data are split into training, validation, and test sets.

## Models
Two hybrid models were developed, integrating **Transformers** and **Autoencoders**:
1. **Model 1**
   - **Accuracy**: 95.29%
   - **Description**: This model achieves high accuracy on normal data but struggles with rare anomalies due to class imbalance. It uses a basic Transformer layer followed by an Autoencoder for reconstruction.
   - **Parameters**: 4 Transformer layers, 128 hidden units, 0.001 learning rate.
2. **Model 2**
   - **Accuracy**: 96.91%
   - **Description**: An enhanced version with deeper Transformer layers and a refined Autoencoder. It better balances precision and recall, improving anomaly detection.
   - **Enhancements**: 4 Transformer layers with 8 attention heads, ReLU activation, dropout 0.2, StepLR Scheuling for decreasing learning rate by a factor of 0.5 after every 5 epochs, label smoothing with a smoothing factor of 0.1, dynamic thresholding.

### 🔥 Model Architecture

   -   **Embedding Layer**: Converts system calls into vector representations.

   -   **Positional Encoding**: Adds sequence information.

   -   **Transformer Encoder**: Learns sequence patterns.

   -   **Transformer Decoder**: Tries to reconstruct input.

   -   **Reconstruction Error**: Used to detect anomalies.

   -   **Multi-Head Attention**: Enhances feature extraction.

   -   **Dropout Layers**: Prevents overfitting.

   -   **Layer Normalization**: Stabilizes training.

### Performance Analysis
- **Accuracy**: Measures overall correctness but is skewed by the predominance of normal data.
- **F1-Score**: Balances precision and recall, critical for rare anomaly detection.
- Model 2 outperforms Model 1, but both F1-scores suggest challenges with imbalanced data.

### 🛠 Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/<your-username>/anomaly-detection-linux.git
   cd anomaly-detection-linux
   ```

2. **Install dependencies (using Conda)**:
   ```bash
   conda env create -f adfa_env.yml
   conda activate adfa_env
   ```
   
3. **Install dependencies(using pip if conda is not installed)**:
   ```bash
   pip install -r requirements.txt
   ```

### 🚀 Future Improvements

   - Implement Dynamic Thresholding based on statistical methods.

   - Extend dataset for better generalization across multiple attack types.

   - Optimize training with Hyperparameter Tuning.

   - Deploy a Real-time Anomaly Detection System using Flask or FastAPI.

   - Integrate Explainability Techniques to interpret model decisions.

### 🏆 Contributing

## We welcome contributions! To get started:

   - Fork the repository.

   - Create a new branch (git checkout -b feature-branch).

   - Commit changes (git commit -m "Added new feature").

   - Push to the branch (git push origin feature-branch).

   - Open a Pull Request.

### License
This project is licensed under the  [BSD 3-Clause "New" or "Revised" License](LICENSE).

### Contact
For questions or collaboration, reach out via GitHub Issues or email <thack7010@duck.com>.