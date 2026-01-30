# Wan2GP

Super Optimized Gradio UI for Wan2.1 video generation, designed for GPU-poor machines (5GB+ VRAM). Generate up to 12 second AI videos with text-to-video and image-to-video modes.

Based on [Wan2GP by deepbeepmeep](https://github.com/deepbeepmeep/Wan2GP).

## Requirements

- NVIDIA GPU with 5GB+ VRAM
- Windows or Linux

## How to Use

1. Click **Install** to set up the environment (clones the repository, installs dependencies, PyTorch, triton, and sageattention).
2. Click **Start** to launch the Gradio web UI.
3. The web UI will open automatically once the server is ready.
4. Use **Advanced > Compiled** mode for faster inference (may not work on all systems).
5. Place LoRA files in the **T2V Loras** or **I2V Loras** folders accessible from the sidebar.

## Features

- Text-to-Video generation (up to 12 seconds)
- Image-to-Video generation
- Multiple image input support
- LoRA support (T2V and I2V)
- Optional compiled mode for faster inference
- Optimized for low VRAM GPUs (5GB+)

## API

Wan2GP exposes a Gradio web interface. You can interact with it programmatically:

### Python

```python
from gradio_client import Client

client = Client("http://127.0.0.1:7860")
result = client.predict(
    prompt="A cat walking on the beach at sunset",
    api_name="/generate"
)
print(result)
```

### JavaScript

```javascript
import { Client } from "@gradio/client";

const client = await Client.connect("http://127.0.0.1:7860");
const result = await client.predict("/generate", {
  prompt: "A cat walking on the beach at sunset",
});
console.log(result.data);
```

### cURL

```bash
curl -X POST http://127.0.0.1:7860/api/generate \
  -H "Content-Type: application/json" \
  -d '{"data": ["A cat walking on the beach at sunset"]}'
```

> **Note:** The port may vary. Check the Pinokio terminal output for the actual URL. The API endpoints depend on the Gradio interface exposed by the app.
