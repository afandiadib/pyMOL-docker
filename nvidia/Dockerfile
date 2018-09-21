FROM nvidia/opengl:1.1-glvnd-devel-ubuntu16.04

MAINTAINER "Adib Afandi bin Abdullah <fendy90.oscura@gmail.com>"

RUN apt-get update && \

# pymol
    apt-get -y install git build-essential python-dev python-pmw libglew-dev freeglut3-dev libpng-dev libfreetype6-dev libxml2-dev libmsgpack-dev python-pyqt5.qtopengl libglm-dev && \
    git clone https://github.com/schrodinger/pymol-open-source.git && \
    cd pymol-open-source && \
    python setup.py install --prefix=/opt/pymol && \

# cleanup
    apt-get -y purge git && \
    apt-get -y autoremove && apt-get -y clean && \
    rm -rf /var/lib/apt/lists/* && \
    rm -rf /pymol-open-source

CMD /opt/pymol/bin/pymol
