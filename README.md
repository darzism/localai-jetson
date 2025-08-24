# LocalAI Jetson Orin Docker Project

This project sets up [LocalAI](https://github.com/go-skynet/LocalAI) on a Jetson Orin device running Ubuntu 22.04 with Jetpack 6.x.

## Requirements

- Jetson Orin board (ARM64, Ubuntu 22.04, Jetpack 6.x)
- Docker & NVIDIA Container Toolkit ([Install Guide](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html))
- At least 16GB RAM

## Setup

1. **Clone this repo**

   ```bash
   git clone <your-repo>
   cd <your-repo>
   ```

2. **Add models**

   Place your preferred LocalAI-compatible models (e.g., `gpt4all-model.bin`) in the `models/` directory.

3. **Edit config.yaml**

   Ensure `config.yaml` points to your model files and sets correct backends.

4. **Run LocalAI**

   ```bash
   docker compose up -d
   ```

   The API will be available at `http://localhost:8080`.

## Notes

- The Docker image is `localai/localai:latest-cuda-arm64` for Jetson Orin (ARM64 + CUDA).
- The container is limited to 15GB RAM, leaving some for the OS.
- For more configuration and advanced usage, refer to [LocalAI documentation](https://github.com/go-skynet/LocalAI).

## Example config.yaml

```yaml
models:
  - name: gpt4all
    backend: llama-cpp
    path: /models/gpt4all-model.bin
```

## Troubleshooting

- Make sure your model file is compatible with LocalAI and the specified backend.
- If Docker fails to access the GPU, check your NVIDIA Container Toolkit installation.
