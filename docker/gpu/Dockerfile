FROM nvidia/cuda:9.0-cudnn7-devel

ENV LANG C.UTF-8
ENV LANGUAGE C.UTF-8
ENV LC_ALL C.UTF-8

RUN apt-get update && apt-get install -y \
    libglib2.0-0 \
    libsm6 \
    libxext-dev \
    libxrender-dev \
    python3-pip \
    wget \
    && rm -rf /var/lib/apt/lists/*

RUN pip3 install -U pip==9.0.3 \
    && pip3 install \
    cython==0.28.3 \
    h5py==2.8.0 \
    imgaug==0.2.6 \
    keras==2.1.6 \
    numpy==1.14.5 \
    opencv-python==3.4.1.15 \
    Pillow==5.1.0 \
    scikit-image==0.13.1 \
    scipy==1.1.0 \
    tensorflow-gpu==1.9.0 \
    && pip3 install \
    jupyter \
    pycocotools \
    && rm -rf ~/.cache/pip

WORKDIR /opt/mrcnn
COPY . .
RUN pip3 install --no-deps .

RUN echo 'jupyter notebook --allow-root --ip="*" --no-browser' > run.sh \
    && chmod +x run.sh
CMD [ "bash", "run.sh" ]