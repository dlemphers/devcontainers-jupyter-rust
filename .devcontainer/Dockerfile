# Base Image: Use a minimal Ubuntu image
FROM ubuntu:20.04

# Set environment variables for non-interactive installations
ENV DEBIAN_FRONTEND=noninteractive
ENV PATH="/root/.cargo/bin:$PATH"

# Accept USER_UID and USER_GID as build arguments
ARG USER_UID=1000
ARG USER_GID=1000

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl \
    python3 \
    python3-pip \
    build-essential \
    libssl-dev \
    pkg-config \
    && apt-get clean

# Install Rust and the Jupyter Rust kernel
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y && \
    rustup install stable && \
    rustup default stable && \
    cargo install evcxr_jupyter && \
    evcxr_jupyter --install

# Install Jupyter Lab
RUN pip install --no-cache-dir notebook jupyterlab

# Create and configure jovyan user with matching UID/GID
RUN if ! getent group $USER_GID > /dev/null 2>&1; then groupadd -g $USER_GID jovyan; fi && \
    if ! id -u jovyan > /dev/null 2>&1; then useradd -m -u $USER_UID -g $USER_GID jovyan; fi && \
    mkdir -p /home/jovyan/work/notebooks && \
    chown -R $USER_UID:$USER_GID /home/jovyan

    
USER jovyan

# Set environment variables for Jupyter
ENV NOTEBOOK_DIR=/home/jovyan/work/notebooks
ENV JUPYTERLAB_WORK_DIR=$NOTEBOOK_DIR

# Default working directory
WORKDIR /home/jovyan/work

# Expose Jupyter port
EXPOSE 8888

# Start Jupyter Lab with the configured notebook directory
CMD ["jupyter-lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--NotebookApp.notebook_dir=/home/jovyan/work/notebooks", "--NotebookApp.token=''", "--NotebookApp.password=''"]
