FROM mcr.microsoft.com/devcontainers/python:3.11-bookworm

# Install system build dependencies required for compiling scikit-learn and typical benchopt solvers
RUN apt-get update \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
       build-essential \
       gfortran \
       libopenblas-dev \
       liblapack-dev \
       git \
       less \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Switch back to the vscode user that the devcontainers base image provides
USER vscode

# Make sure pip is up-to-date in the image build layer (helps speed up container start)
RUN pip install --no-cache-dir --upgrade pip

# Default workdir will be overriden by the devcontainer.json, but keeping a sane fallback
WORKDIR /workspaces 