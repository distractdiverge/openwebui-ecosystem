# Local ChatGPT Ecosystem with Ollama

A Docker Compose setup for running a local ChatGPT-like ecosystem using Ollama for local LLM inference and Open WebUI for the chat interface.

## Features

- 🚀 **Local LLM Inference** using Ollama
- 💬 **Modern Web Interface** with Open WebUI
- 🔒 **Private & Secure** - All data stays on your machine
- 🐳 **Easy Setup** with Docker Compose
- 🤖 **Multiple Models** - Download and switch between different LLM models

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) (v20.10.0 or higher)
- [Docker Compose](https://docs.docker.com/compose/install/) (v2.0.0 or higher)
- At least 8GB RAM (16GB+ recommended for larger models)
- At least 10GB free disk space (for models)

## Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/openwebui-ecosystem.git
   cd openwebui-ecosystem
   ```

2. Start the services:
   ```bash
   docker-compose up -d
   ```

3. Access the web interface at: http://localhost:3000

4. (Optional) Download models through the web interface or using the Ollama CLI:
   ```bash
   # Access the Ollama container
   docker exec -it ollama ollama pull mistral
   ```

## Services

- **Open WebUI** (http://localhost:3000)
  - Modern web interface for interacting with LLMs
  - User authentication (disabled by default)
  - Conversation history
  - Model management

- **Ollama** (http://localhost:11434)
  - Local LLM server
  - Supports multiple models
  - Optimized for CPU/GPU acceleration

## Managing Models

### Available Models

You can use various models with Ollama. Some popular ones include:

- `mistral` - Small, fast model (good for testing)
- `llama2` - Meta's LLaMA 2
- `codellama` - Specialized for code generation
- `mixtral` - High-quality responses (requires more RAM)

### Downloading Models

1. Through the Open WebUI interface (Settings > Models)
2. Using the Ollama CLI:
   ```bash
   docker exec -it ollama ollama pull <model-name>
   ```
   Example:
   ```bash
   docker exec -it ollama ollama pull mistral
   ```

## Configuration

### Environment Variables

Create a `.env` file to customize the setup:

```env
# Open WebUI
OPEN_WEBUI_AUTH_ENABLED=false
# OLLAMA_API_BASE_URL=http://ollama:11434

# Ollama
# OLLAMA_ORIGINS=*
```

### Ports

- **3000**: Open WebUI interface
- **11434**: Ollama API

## Updating

To update the services to their latest versions:

```bash
docker-compose pull
docker-compose up -d --force-recreate
```

## Troubleshooting

### Common Issues

1. **Out of Memory**
   - Try smaller models
   - Allocate more RAM to Docker
   - Close other memory-intensive applications

2. **Port Conflicts**
   - Check if ports 3000 or 11434 are already in use
   - Modify the ports in `docker-compose.yml` if needed

3. **Model Download Issues**
   - Check your internet connection
   - Ensure you have enough disk space
   - Try pulling the model manually using the Ollama CLI

## License

MIT

## Acknowledgements

- [Open WebUI](https://github.com/open-webui/open-webui)
- [Ollama](https://ollama.ai/)
- [Docker](https://www.docker.com/)
