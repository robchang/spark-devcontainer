FROM nvcr.io/nvidia/tensorrt-llm/release:spark-single-gpu-dev

# Set environment variables
ENV PYTHONPATH=/workspace
ENV PATH=/workspace/.venv/bin:$PATH

# Create virtual environment
RUN python3 -m venv /workspace/.venv
ENV VIRTUAL_ENV=/workspace/.venv
ENV PATH=/workspace/.venv/bin:$PATH

# Upgrade pip
RUN pip install --upgrade pip

# Build llama.cpp with CUDA support
RUN git clone https://github.com/ggerganov/llama.cpp.git /opt/llama.cpp && \
    cd /opt/llama.cpp && \
    cmake -B build -DGGML_CUDA=ON && \
    cmake --build build --config Release -j$(nproc) && \
    ln -s /opt/llama.cpp/build/bin/llama-cli /usr/local/bin/llama-cli && \
    ln -s /opt/llama.cpp/build/bin/llama-server /usr/local/bin/llama-server
