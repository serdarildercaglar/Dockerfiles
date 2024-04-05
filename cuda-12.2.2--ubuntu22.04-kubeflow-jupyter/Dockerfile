# Stage 1: Builder/Compiler
FROM nvidia/cuda:12.2.2-base-ubuntu22.04 AS builder
ARG DEBIAN_FRONTEND=noninteractive

# Install dependencies
# Update and install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    python3 \
    python3-pip \
    python3-setuptools \
    python3-wheel \
    python3-dev libprotobuf-dev protobuf-compiler \
    && rm -rf /var/lib/apt/lists/*

# Install Python virtual environment
RUN python3 -m pip install --upgrade pip setuptools


# RUN pip3 install --pre torch --index-url https://download.pytorch.org/whl/nightly/cpu
RUN pip3 install onnxruntime-gpu==1.17.1 --extra-index-url https://aiinfra.pkgs.visualstudio.com/PublicPackages/_packaging/onnxruntime-cuda-12/pypi/simple/

COPY ./nltk_data /root/nltk_data
COPY ./ ./
# Delete the nltk_data folder
RUN rm -rf nltk_data
RUN pip3 install --no-cache-dir -r requirements.txt
EXPOSE 8080

# CMD [ "python3", "kserve_main.py" ]
# CMD ["sh","-c", "jupyter lab --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]


CMD ["sh","-c", "jupyter lab --notebook-dir=/home/jovyan --ip=0.0.0.0 --no-browser --allow-root --port=8888 --NotebookApp.token='' --NotebookApp.password='' --NotebookApp.allow_origin='*' --NotebookApp.base_url=${NB_PREFIX}"]
