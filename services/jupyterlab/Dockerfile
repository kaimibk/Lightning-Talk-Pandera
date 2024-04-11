# Build requires the root as the context as it COPYs from a shared library.
FROM quay.io/jupyter/scipy-notebook:lab-4.1.2
WORKDIR /app
LABEL maintainer="Kahihikolo_Kaimi@bah.com"

# Install all slow-to-install dependencies
COPY ./services/jupyterlab/requirements/large_requirements.txt ./requirements/large_requirements.txt
RUN --mount=type=cache,target=/home/jovyan/.cache/pip,sharing=locked,uid=1000,gid=100 \
    --mount=type=cache,target=/opt/conda/pkgs,sharing=locked,uid=1000,gid=100 \
    pip install -r ./requirements/large_requirements.txt

# Install all fast pypi dependencies
COPY ./services/jupyterlab/requirements/requirements.txt ./requirements/requirements.txt
RUN --mount=type=cache,target=/home/jovyan/.cache/pip,sharing=locked,uid=1000,gid=100 \
    --mount=type=cache,target=/opt/conda/pkgs,sharing=locked,uid=1000,gid=100 \
    pip install -r ./requirements/requirements.txt

ENV NOTEBOOK_PATH=/app/notebooks