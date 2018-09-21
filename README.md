# pyMOL Container

Two versions available: NVIDIA and NOUVEAU-supported container. For NVIDIA support, you need to install NVIDIA driver on host and install nvidia-docker2.

To download:
  1. docker pull afandiadib/pymol:nvidia
  2. docker pull afandiadib/pymol:nouveau

Example of usage:

### nouveau-supported pyMOL container

     docker run --rm --user=$(id -u) \
                --workdir=`pwd` \
                --env=DISPLAY \
                --volume=/home/$USER:/home/$USER \
                --volume=/media:/media \
                --volume=/mnt:/mnt \
                --volume=/etc/group:/etc/group:ro \
                --volume=/etc/passwd:/etc/passwd:ro \
                --volume=/etc/shadow:/etc/shadow:ro \
                --volume=/etc/sudoers.d:/etc/sudoers.d:ro \
                --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw \
                --volume=/usr/share/fonts/:/usr/share/fonts/:ro \
                --volume=/usr/share/icons:/usr/share/icons \
                --device=/dev/dri \
                afandiadib/pymol:nouveau

If permission denied, you need to change ownership of /dev/dri on host for gpu acceleration.
sudo chown -R $USER /dev/dri


### nvidia-supported pyMOL container

    docker run --rm --user=$(id -u) \
               --workdir=`pwd` \
               --env=DISPLAY \
               --volume=/home/$USER:/home/$USER \
               --volume=/media:/media --volume=/mnt:/mnt \
               --volume=/etc/group:/etc/group:ro \
               --volume=/etc/passwd:/etc/passwd:ro \
               --volume=/etc/shadow:/etc/shadow:ro \
               --volume=/etc/sudoers.d:/etc/sudoers.d:ro \
               --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw \
               --volume=/usr/share/fonts/:/usr/share/fonts/:ro \
               --volume=/usr/share/icons:/usr/share/icons \
               --runtime=nvidia \
               afandiadib/pymol:nvidia



