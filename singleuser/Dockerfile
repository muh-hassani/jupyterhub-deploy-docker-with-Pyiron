FROM jupyter/minimal-notebook:latest
RUN /opt/conda/bin/conda install jupyterhub && \
    /opt/conda/bin/conda install -c conda-forge pyiron && \
    /opt/conda/bin/conda install -c conda-forge lammps && \
    /opt/conda/bin/conda install -c conda-forge nodejs nglview && \
    jupyter labextension install @jupyter-widgets/jupyterlab-manager --no-build && \
    jupyter labextension install nglview-js-widgets
