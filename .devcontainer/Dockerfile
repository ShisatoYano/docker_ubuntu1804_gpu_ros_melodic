# pull base image to use GPU
FROM nvidia/opengl:base-ubuntu18.04

# set as non interactive
ARG DEBIAN_FRONTEND=noninteractive

# install common tools
RUN apt update && apt install -y \
git \
vim \
wget \
gdb \
curl \
lsb-release \
&& apt clean \ 
&& rm -rf /var/lib/apt/lists/*

# add user
ARG UID=2000
ARG GID=2000
RUN groupadd -g $GID dev-user \
&& useradd -m -d /home/dev-user -s /bin/bash -u $UID -g $GID dev-user

# ROS Melodic
# setup your sources.list
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'

# setup your keys
RUN curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add -

# installation
RUN apt update \
&& apt install -y ros-melodic-desktop-full \
&& apt search ros-melodic

# environment setup
RUN echo "source /opt/ros/melodic/setup.bash" >> /home/dev-user/.bashrc
RUN mkdir -p /home/dev-user/catkin_ws/src
RUN cd /home/dev-user/catkin_ws && /bin/bash -c "source /opt/ros/melodic/setup.bash; catkin_make"
RUN echo "source /home/dev-user/catkin_ws/devel/setup.bash" >> /home/dev-user/.bashrc
RUN /bin/bash -c "source /home/dev-user/catkin_ws/devel/setup.bash"

# dependencies for building packages
# initialize rosdep
RUN apt update \
&& apt install -y python-rosdep \ 
python-rosinstall \
python-rosinstall-generator \
python-wstool \
build-essential \
&& cd /home/dev-user/catkin_ws \
&& rosdep init \
&& rosdep update

# set user
USER dev-user