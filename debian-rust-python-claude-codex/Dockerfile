FROM rust:trixie

ENV DEBIAN_FRONTEND=noninteractive
ENV USE_BUILTIN_RIPGREP=0
ENV PATH="/root/.local/bin:/usr/local/cargo/bin/:${PATH}"

# Usar bash
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Agregar ruta cargo para tmux
RUN echo 'export PATH="$HOME/.local/bin:/usr/local/cargo/bin/:$PATH"' >> ~/.bashrc

# Agregar mi alias favorito
RUN echo 'alias l="ls -lAh"' >> ~/.bashrc

# Instalar dependencias
RUN apt-get update && apt-get install -y \
    build-essential bash git tmux \
    ripgrep openssh-client ca-certificates wget curl \
    python3 python3-venv python3-pip unzip

# Instalar nvm
ENV BASH_ENV="/root/.bash_env"
RUN touch "${BASH_ENV}"
RUN echo '. "${BASH_ENV}"' >> ~/.bashrc
RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.4/install.sh | PROFILE="${BASH_ENV}" bash
RUN echo node > .nvmrc

# Instalar Node.js LTS
RUN nvm install --lts

# Instalar uv (Python package manager)
RUN curl -fsSL https://astral.sh/uv/install.sh | bash

# Instalar claude
RUN curl -fsSL https://claude.ai/install.sh | bash

# Instalar codex
RUN npm install -g @openai/codex

WORKDIR /workspace

CMD ["bash"]
