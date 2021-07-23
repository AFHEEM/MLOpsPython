FROM conda/miniconda3

LABEL org.label-schema.vendor = "Microsoft" \
    org.label-schema.url = "https://hub.docker.com/r/microsoft/mlopspython" \
    org.label-schema.vcs-url = "https://github.com/microsoft/MLOpsPython"

COPY diabetes_regression/ci_dependencies.yml /setup/

# activate environment
ENV PATH /usr/local/envs/mlopspython_ci/bin:$PATH

RUN conda update -n base -c defaults conda && \
    conda install python=3.7.5 && \
    pip install cryptography==3.1 && \
    conda env create -f /setup/ci_dependencies.yml && \
    pip install cryptography==3.1 && \
    /bin/bash -c "source activate mlopspython_ci" && \
    conda install cryptography=3.1 && \
    pip install cryptography==3.1 && \
    az --version && \
    chmod -R 777 /usr/local/envs/mlopspython_ci/lib/python3.7
