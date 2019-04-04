FROM discoenv/jupyter-lab:beta

USER root

# Update the packages
RUN apt-get update \
    && apt-get clean \
    && apt-get install -y swig \
    && rm -rf /usr/lib/apt/lists/*

USER jovyan

# Install auto-sklearn dependencies
RUN conda install cython gxx_linux-64 gcc_linux-64 ipywidgets \
                  matplotlib numpy==1.16 pandas scipy>=0.14.1 \
                  scikit-learn>=0.19,<0.20 seaborn

RUN pip install auto-sklearn==0.4.0

WORKDIR /home/jovyan

COPY entry.sh /bin
RUN mkdir /home/jovyan/.irods

ENTRYPOINT ["/bin/entry.sh"]
