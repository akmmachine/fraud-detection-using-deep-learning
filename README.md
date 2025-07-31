Credit Card Fraud Detection using Autoencoder & Graph Neural Networks
-
This project implements a hybrid deep learning system to detect fraudulent credit card transactions. It leverages a combination of an Autoencoder for anomaly detection and a Graph Neural Network (GNN) to analyze the relationships between transactions, providing a robust and comprehensive fraud detection solution.

The entire application is wrapped in a user-friendly web interface built with Streamlit.

🎥 Live Demo
-
A brief GIF or video of the application in action would be ideal here.

✨ Features
-
Hybrid Model Approach: Combines the strengths of Autoencoders (for identifying anomalous transactions) and GNNs (for capturing complex relational patterns).

Real-Time Prediction: Provides instant fraud analysis for new transaction data entered by the user.

Interactive Web Interface: A clean and intuitive UI built with Streamlit for easy interaction and visualization.

Model Insights: Includes visualizations like confusion matrices and reconstruction error distributions to help understand model performance.

🤖 Models & Methodology
-
The system uses a two-pronged approach to identify potentially fraudulent activities.

1. Autoencoder for Anomaly Detection
   -

Concept: An Autoencoder is an unsupervised neural network trained to reconstruct its input. For this project, it is trained exclusively on legitimate transactions.

Mechanism: When a new transaction is processed, the Autoencoder attempts to reconstruct it.

If the transaction is legitimate, the model can reconstruct it accurately, resulting in a low reconstruction error.

If the transaction is fraudulent, it will deviate from the learned "normal" patterns. The model will struggle to reconstruct it, leading to a high reconstruction error.

Verdict: A predefined threshold is used on the reconstruction error to classify a transaction as either LEGITIMATE or FRAUDULENT.

2. Graph Neural Network (GCN) for Relational Analysis
   -
Concept: Transactions are not isolated events. They are connected through shared attributes like card numbers, merchants, IP addresses, and locations. A GNN is perfect for learning from this kind of graph-structured data.

Mechanism:

We construct a graph where transactions are nodes.

Edges are created between nodes that share key features (e.g., same card number, same merchant).

The GCN learns patterns from the connections in this graph. It can identify suspicious networks, such as a single card being used at multiple distant locations in a short time frame.

Verdict: The GCN classifies a new transaction based on its connections and neighborhood within the graph, identifying if it belongs to a known or emerging fraudulent pattern.


⚙️ Setup and Installation
-
Clone the repository:

git clone [https://github.com/your-username/fraud-detection-using-deep-learning.git](https://github.com/your-username/fraud-detection-using-deep-learning.git)
cd fraud-detection-using-deep-learning

Create a virtual environment (recommended):

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

Install the required dependencies:

pip install -r requirements.txt

Note: You may need to install PyTorch and PyTorch Geometric separately depending on your CUDA version. Please refer to their official websites for specific installation commands.

▶️ How to Run the Application
-
Once the setup is complete, you can run the Streamlit application with the following command:

streamlit run app.py

This will open the application in your default web browser, where you can input transaction details to get a fraud prediction.

📋 Dependencies
-
The main libraries used in this project are:

streamlit
torch
torch_geometric
pandas
numpy

scikit-learn

joblib

Pillow
