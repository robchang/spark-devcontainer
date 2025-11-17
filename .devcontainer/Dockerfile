# Use the NVIDIA base image
FROM nvcr.io/nvidia/tensorrt-llm/release:spark-single-gpu-dev

# Set working directory
WORKDIR /workspace

# Install additional system dependencies if needed
# RUN apt-get update && apt-get install -y \
#     build-essential \
#     cmake \
#     git \
#     && rm -rf /var/lib/apt/lists/*

# Set environment variables
ENV PYTHONPATH=/workspace
ENV PATH=/workspace/.venv/bin:$PATH

# Create virtual environment
RUN python3 -m venv /workspace/.venv
ENV VIRTUAL_ENV=/workspace/.venv
ENV PATH=/workspace/.venv/bin:$PATH

# Upgrade pip
RUN pip install --upgrade pip

# Install Python dependencies 
RUN pip install gradio 

# Set default command
CMD ["bash"]
