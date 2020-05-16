FROM ufoym/deepo:all-jupyter
ENV LANG C.UTF-8
RUN APT_INSTALL="apt-get install -y --no-install-recommends" && \
    PIP_INSTALL="python -m pip install --upgrade --no-cache-dir --retries 10 --timeout 60" && \
    GIT_CLONE="git clone --depth 10" && \

    rm -rf /var/lib/apt/lists/* \
           /etc/apt/sources.list.d/cuda.list \
           /etc/apt/sources.list.d/nvidia-ml.list && \

    apt-get update && \
    DEBIAN_FRONTEND=noninteractive $APT_INSTALL \
        software-properties-common \
        && \
    add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main" && \
    apt-get update && \

# ==================================================================
# My Extra Package
# ------------------------------------------------------------------

    $PIP_INSTALL \
        mlfinlab \
        numba \
        statsmodels \
        arch \
        pykalman \
        plotly \
        plotnine \
        pymc3 \
        ipywidgets \
        && \

# ==================================================================
# jupyter related
# ------------------------------------------------------------------

    $PIP_INSTALL \
        jupyterlab &&\

    curl -sL https://deb.nodesource.com/setup_14.x | bash - &&\
    $APT_INSTALL  nodejs &&\
     
 
    jupyter labextension install jupyterlab-plotly@4.7.1
        
        


