FROM node:lts-trixie

ENV DEBIAN_FRONTEND=noninteractive
ENV USE_BUILTIN_RIPGREP=0
ENV PATH="/root/.local/bin:${PATH}"

# Usar bash
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Agregar mi alias favorito
RUN echo 'alias l="ls -lAh"' >> ~/.bashrc

# Instalar dependencias
RUN apt-get update && apt-get install -y \
    build-essential bash git tmux \
    ripgrep openssh-client ca-certificates wget curl \
    python3 python3-venv python3-pip unzip

# Instalar uv (Python Package Manager)
RUN curl -LsSf https://astral.sh/uv/install.sh | bash

# Instalar Claude Code CLI
RUN curl -fsSL https://claude.ai/install.sh | bash

# Instalar OpenAI Codex
RUN npm install -g @openai/codex

WORKDIR /workspace

CMD ["bash"]
