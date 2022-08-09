ARG BASE_IMAGE="scipy-notebook"
ARG IMAGE_TAG="latest"
FROM jupyter/${BASE_IMAGE}:${IMAGE_TAG}}

# USER root
# RUN apt-get update --yes && \
#     apt-get install --yes --no-install-recommends \
#     <packages-you-want> && \
#     apt-get clean && rm -rf /var/lib/apt/lists/*

USER ${NB_UID}

# alternative:
# COPY requirements.txt /tmp/requirements.txt
# RUN pip3 --disable-pip-version-check --no-cache-dir install -r /tmp/requirements.txt \
#    && rm -rf /tmp/pip-tmp

RUN mamba install --quiet --yes \
    'black' \
    'flake8' && \
    mamba clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}" 

CMD ["/bin/bash"]
