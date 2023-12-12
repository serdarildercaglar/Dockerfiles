# Stage 1: Builder/Compiler
FROM nvidia/cuda:11.7.1-cudnn8-runtime-ubuntu22.04 AS builder

ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies
# Update and install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    python3 \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    python3.10-venv \
    && rm -rf /var/lib/apt/lists/*

# Install Python virtual environment
RUN python3 -m pip install --upgrade pip setuptools
RUN python3 -m pip install virtualenv 
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"



# copy requirements.txt to the docker image

COPY requirements.txt .
RUN pip3 install --no-cache-dir -r requirements.txt

# Stage 2: Runtime
FROM nvidia/cuda:11.7.1-cudnn8-runtime-ubuntu22.04

RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    cmake \
    python3 \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    python3.10-venv \
    && rm -rf /var/lib/apt/lists/*

# copy the python virtual environment from the builder stage
COPY --from=builder /opt/venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"
EXPOSE 8080

# CMD ["sh","-c", "jupyter lab --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]