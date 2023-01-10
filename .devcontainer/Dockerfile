FROM ghcr.io/airic-polimi/python-devcontainer-base-dockerimage:main

# Base ENV variables (anchor folders)
ARG WORKSPACE_FOLDER
ENV WORKSPACE_FOLDER=${WORKSPACE_FOLDER}
ENV PYTHONPATH=${WORKSPACE_PATH}/packages:${PYTHONPATH}

COPY --chown=vscode:vscode packages/ $WORKSPACE_FOLDER/packages/

# Install additional python versions (as requested by the packages)
RUN for p in $WORKSPACE_FOLDER/packages/*/; do \
    if [ -f $p/.python-version ]; then \
    pyenv install --skip-existing `cat $p/.python-version`; \
    fi; \
    done

# Use PDM to install dependencies for all packages
RUN for p in $WORKSPACE_FOLDER/packages/*/; do cd $p; pdm install; done
