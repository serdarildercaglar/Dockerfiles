# Kubeflow Jupyter Notebooks GPU-Enabled ONNX Runtime Docker Image

This repository contains a GPU-enabled Docker image for running ONNX models in Kubeflow Jupyter notebooks. The image itself is tagged as "serdarildercaglar/kubeflow-onnxruntime-gpu:cuda-117-cudnn8-kserve-0.11-kf-jupyter".

## Image Contents

- Ubuntu 22.04
- CUDA 11.7.1
- cuDNN 8
- PyTorch 1.13
- ONNX Runtime
- Jupyter compatible with Kubeflow 1.5  

## Usage

1. Pull the image locally: serdarildercaglar/kubeflow-onnxruntime-gpu:cuda-117-cudnn8-kserve-011-kubeflow



2. Deploy a notebook in your Kubeflow cluster and use the image

## Contributing

Bugs, feature requests and contributions are warmly welcomed! Please open an issue or PR.

## License

This project is licensed under the MIT license.
