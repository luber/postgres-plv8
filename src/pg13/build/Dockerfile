FROM postgres:13

RUN apt-get update && apt-get upgrade \
    && apt-get install -y wget git curl glib2.0 libc++-dev libc++abi-dev libglib2.0-dev libtinfo5 ninja-build \
       python python-pip pkg-config libv8-dev libncurses5-dev libncursesw5-dev \
       postgresql-server-dev-13