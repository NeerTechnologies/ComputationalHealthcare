FROM tensorflow/tensorflow:0.11.0

MAINTAINER Akshay Bhat <akshayubhat@gmail.com>

RUN add-apt-repository ppa:george-edison55/cmake-3.x && apt-get update && apt-get install -y \
		bc \
		build-essential \
		cmake \
		curl \
		g++ \
		gfortran \
		git \
		libffi-dev \
		libssl-dev \
		libtiff5-dev \
		libzmq3-dev \
		nano \
		pkg-config \
		python-pip \
		python-dev \
		software-properties-common \
		unzip \
		vim \
		wget \
		zlib1g-dev \
		libboost-all-dev \
		libgflags-dev \
		libgoogle-glog-dev \
		libsnappy-dev \
		libleveldb-dev \
		libprotobuf-dev \
		protobuf-compiler \
		&& \
	apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y libpq-dev && \
	apt-get clean && \
	apt-get autoremove && \
	rm -rf /var/lib/apt/lists/*
RUN pip install --upgrade pip \
                          fabric \
                          django \
                          jinja \
                          jinja2 \
                          djangorestframework \
                          markdown \
                          django-filter \
                          "celery==3.1.23" \
                          "django-celery==3.1.17" \
                          "dj-database-url==0.4.0" \
                          "whitenoise==2.0.6" \
                          raven \
                          psycopg2 \
                          requests \
                          plyvel \
                          pandas \
                          boto3 \
                          protobuf \
                          humanize

COPY CH.zip /root/data/CH.zip
RUN unzip /root/data/CH.zip -d /root/data/
RUN  git clone https://github.com/akshayubhat/ComputationalHealthcare /root/ComputationalHealthcare
WORKDIR "/root/ComputationalHealthcare"
COPY config.json .
RUN fab compile_protocols
RUN fab compile_cpp_code
VOLUME  ["/root/data"]

