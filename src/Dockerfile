FROM continuumio/anaconda3:2020.11

WORKDIR /workdir
EXPOSE 8888

# jupyter lab extensions. 
RUN conda install -c anaconda -y nodejs && \ 
    conda install -c conda-forge jupyterlab-snippets && \
    conda install -c conda-forge jupyterlab-git -y && \
    jupyter labextension install jupyterlab-plotly@4.14.3 --no-build && \
    jupyter labextension install @jupyterlab/toc --no-build && \
    jupyter labextension install @axlair/jupyterlab_vim --no-build && \
    jupyter lab build

# python package installation. 
RUN pip install japanize-matplotlib 
RUN pip install pymc3==3.10.0 && pip install watermark

# install gcc 
RUN apt update 
RUN apt install build-essential -y

# install vim 
RUN apt-get update && \
    apt-get install -y vim

RUN echo "alias jpt_lab='jupyter lab --ip=0.0.0.0 --port=8888 --no-browser --allow-root '" >> /root/.bashrc


