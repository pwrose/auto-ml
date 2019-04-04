FROM discoenv/jupyter-lab:beta

USER root

# Update the packages and install swig
RUN apt-get update \
    && apt-get clean \
    && apt-get install -y build-essential swig \
    && rm -rf /usr/lib/apt/lists/*

USER jovyan

# Download auto-sklearn dependencies
RUN curl -O https://raw.githubusercontent.com/automl/auto-sklearn/master/requirements.txt
RUN mv requirements.txt  /tmp

# Install auto-sklearn dependencies
RUN pip install -r /tmp/requirements.txt

RUN pip install auto-sklearn

WORKDIR /home/jovyan

COPY entry.sh /bin
RUN mkdir /home/jovyan/.irods

ENTRYPOINT ["/bin/entry.sh"]
