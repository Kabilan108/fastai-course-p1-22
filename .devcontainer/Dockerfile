FROM mcr.microsoft.com/devcontainers/python:0-3.10

COPY requirements.txt /workspaces/fastai-course-p1-22

RUN echo "(*) Installing tools..." \
    && su - vscode -c "pip install -r /tmp/requirements.txt" \
    && apt-get update \
    && apt-get -y install --no-install-recommends graphviz

COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/uv

ENV PATH="/home/vscode/.local/bin:${PATH}"

WORKDIR /workspaces/fastai-course-p1-22

RUN uv venv --python 3.11 && uv pip install -r requirements.txt

COPY welcome-message.txt /usr/local/etc/vscode-dev-containers/first-run-notice.txt
