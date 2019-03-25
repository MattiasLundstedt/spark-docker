FROM spark-base:2.4.0

# Set the directory for Jupyter notebooks
ARG NOTEBOOKS_DIR=/opt/notebooks
WORKDIR ${NOTEBOOKS_DIR}

ENV PYSPARK_PYTHON=python3 PYSPARK_DRIVER_PYTHON=python3

# Install dependencies and run Jupyter. Jupyter will be available in the host on 127.0.0.1:8888
RUN pip install pyspark jupyter
CMD ["jupyter", "notebook", "--ip", "0.0.0.0", "--no-browser", "--allow-root"]
