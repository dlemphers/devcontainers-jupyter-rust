# Start with a lightweight base image
FROM python:3.9-slim

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive \
    PYTHONUNBUFFERED=1 \
    PATH="/root/.cargo/bin:$PATH" \
    CARGO_HOME="/root/.cargo" \
    RUSTUP_HOME="/root/.rustup"

# Install system dependencies and Rust
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3 \
    python3-pip \
    curl \
    build-essential \
    libssl-dev \
    pkg-config \
    && apt-get clean && rm -rf /var/lib/apt/lists/* && \
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y && \
    rustup install stable && \
    rustup default stable && \
    pip install --no-cache-dir notebook jupyterlab

# Install evcxr_jupyter
RUN cargo install evcxr_jupyter && \
    evcxr_jupyter --install

# Expose the Jupyter port
EXPOSE 8888
