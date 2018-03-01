Bootstrap: shub
From: singularityhub/ubuntu

%files
  /braintree/home/jjpr/dev/simpler_dldata      /home/simpler_dldata  # 

%environment
  DEBIAN_FRONTEND=noninteractive
  export DEBIAN_FRONTEND=noninteractive

%labels
  AUTHOR jjpr@mit.edu

%post
  export DEBIAN_FRONTEND=noninteractive
  apt-get update && apt-get install -y --no-install-recommends \
    bison \
    blender \
    build-essential \
    flex \
    git \
    libgl1-mesa-dev \
    libsdl1.2-dev \
    libtiff5-dev \
    python-dev \
    python-pip \
    wget \
    && rm -rf /var/lib/apt/lists/*

    
  pip install --upgrade pip
  pip install --upgrade setuptools

  pip install boto
  pip install cython
  pip install matplotlib
  pip install numexpr
  pip install numpy
  pip install pandas
  pip install Pillow
  pip install pymongo
  pip install scikit-image
  pip install scikit-learn
  pip install scipy
  pip install scipy-stack
  pip install tables
  pip install tornado
  pip install tqdm
  pip install xarray

  pip install git+https://github.com/yamins81/scikit-data.git#egg=skdata
  pip install git+https://github.com/jaberg/pyll.git#egg=pyll
  pip install git+https://github.com/yamins81/yamutils.git#egg=yamutils
  pip install git+https://github.com/dicarlolab/bangmetric.git#egg=bangmetric

  export PATH_TO_GENTHOR=/home/genthor
  mkdir -m 777 $PATH_TO_GENTHOR

  cd /home
  git clone https://github.com/dicarlolab/genthor.git
  git clone https://github.com/yamins81/tabular.git
  # wget https://www.panda3d.org/download/panda3d-1.9.4/panda3d-1.9.4.tar.gz
  # tar -zxvf panda3d-1.9.4.tar.gz
  wget https://www.panda3d.org/download/panda3d-1.8.1/panda3d-1.8.1.tar.gz
  tar -zxvf panda3d-1.8.1.tar.gz

  cd /home/panda3d-1.8.1
  python makepanda/makepanda.py --everything --no-vision
  python makepanda/installpanda.py
  sed -i 's/load-display pandagl$/#load-display pandagl/' /etc/Config.prc
  sed -i 's/#load-display p3tinydisplay$/load-display p3tinydisplay/' /etc/Config.prc

  cd /home/tabular
  sed -i.bak -e '39,54d' setup.py
  python setup.py install

  cd /home/simpler_dldata
  pip install . 

  cd $PATH_TO_GENTHOR
  sed -i.bak -e '39,54d' setup.py
  python setup.py install

  ldconfig
