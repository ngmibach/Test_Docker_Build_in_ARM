FROM ubuntu:24.04
RUN apt-get update && apt-get install -y --no-install-recommends \
        gnupg2 locales && \
    locale-gen en_US en_US.UTF-8 && \
    update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8 && \
    export LANG=en_US.UTF-8 && \
    rm -rf /var/lib/apt/lists/*

RUN curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg && \
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" > /etc/apt/sources.list.d/ros2.list

RUN apt-get update && apt-get install -y --no-install-recommends \
        pkg-config cmake-extras \
        libboost-all-dev libboost-dev libboost-filesystem-dev libboost-program-options-dev libboost-system-dev \
        libboost-serialization-dev libboost-date-time-dev libboost-regex-dev libboost-thread-dev  \
        libx11-dev libxaw7-dev libxrandr-dev libgl1-mesa-dev libglu1-mesa-dev libglew-dev \
        libgles2-mesa-dev libopengl-dev libfreetype-dev libfreetype6-dev libfontconfig1-dev libfmt-dev \
        qtbase5-dev qtchooser qt5-qmake qtbase5-dev-tools libqt5core5a libqt5gui5 libqt5opengl5 libqt5widgets5 \
        libxcursor-dev libxinerama-dev libxi-dev libyaml-cpp-dev libassimp-dev libzzip-dev freeglut3-dev \
        libpng-dev libjpeg-dev python3-pyqt5.qtwebengine \
        libbullet-dev libasio-dev libtinyxml2-dev libeigen3-dev libacl1-dev \
        libconsole-bridge-dev libfmt-dev \
        libqhull-dev libfcl-dev liboctomap-dev liblttng-ust-dev libcunit1-dev \
        libssl-dev \
        python3-pip python3-empy python3-yaml python3-pytest-cov \
        python3-colcon-common-extensions \
    && rm -rf /var/lib/apt/lists/*

# Install binary ROS packages
RUN apt-get update && apt-get install -y --no-install-recommends \
    ros-jazzy-ros-base \
    ros-jazzy-vision-msgs \
    ros-jazzy-ackermann-msgs \
    ros-jazzy-example-interfaces \
    ros-jazzy-image-transport-plugins \
    ros-jazzy-rviz2 \
    ros-jazzy-rmw-fastrtps-cpp \
    ros-jazzy-xacro \
    ros-jazzy-ros2-control \
    ros-jazzy-ros2-controllers \
    ros-jazzy-gripper-controllers \
    ros-jazzy-teleop-twist-keyboard \
    ros-jazzy-ros-gz \
    ros-jazzy-webots-ros2 \
    ros-jazzy-simulation-interfaces \
    && rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --no-cache-dir --no-deps --break-system-packages \
        empy numpy "pybind11[global]" PyYAML \
        argcomplete \
        flake8-blind-except flake8-builtins flake8-class-newline \
        flake8-comprehensions flake8-deprecated flake8-docstrings \
        flake8-import-order flake8-quotes \
        pytest pytest-repeat pytest-rerunfailures lark