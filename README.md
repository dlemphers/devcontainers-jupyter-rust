# Jupyter-Based Development Environment

This project is a **Jupyter-based DevContainer** designed to provide a seamless and reproducible development environment for data exploration and backend development using Python. The environment is containerized using Docker, ensuring consistency across systems and easy setup.

---

## **Features**

- **Jupyter Lab**:
  - Automatically opens in the `notebooks` folder for organized management of notebooks.
  - Includes popular Python libraries for data science and backend development.
  - Fully supports Jupyter Lab extensions to enhance productivity.

- **Python Environment**:
  - Python dependencies are managed via `requirements.txt`.
  - Includes common libraries such as `numpy`, `pandas`, `matplotlib`, `scikit-learn`, and more (customizable).

- **VS Code DevContainer**:
  - Configured for use with Visual Studio Code’s **Remote - Containers** feature.
  - Includes extensions for Python, Jupyter, and Docker to provide a robust development experience.

---

## **Setup Instructions**

### **Requirements**
1. **Docker**: Ensure Docker is installed and running on your system.
   - [Install Docker](https://docs.docker.com/get-docker/)
2. **Visual Studio Code**: Install VS Code and the **Dev Containers** extension.
   - [Install VS Code](https://code.visualstudio.com/)
   - [Install Dev Containers Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

---

### **Quick Start**
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
