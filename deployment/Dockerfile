FROM databricksruntime/standard:10.4-LTS

ENV PATH /databricks/conda/bin:$PATH

RUN wget -q https://repo.continuum.io/miniconda/Miniconda3-py38_4.9.2-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p /databricks/conda && \
    rm miniconda.sh && \
    # Source conda.sh for all login and interactive shells.
    ln -s /databricks/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /etc/profile.d/conda.sh" >> ~/.bashrc && \
    # Set always_yes for non-interactive shells.
    conda config --system --set always_yes True && \
    conda clean --all

COPY conda-env.yml /tmp/conda-env.yml

RUN conda env create --file /tmp/conda-env.yml && \
    rm -f /tmp/conda-env.yml && \
    rm -rf $HOME/.cache/pip/*

ENV DEFAULT_DATABRICKS_ROOT_CONDA_ENV=databricks