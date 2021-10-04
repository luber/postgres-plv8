FROM postgres:14

RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y wget git curl glib2.0 libc++-dev libc++abi-dev libglib2.0-dev libtinfo5 ninja-build \
       python2 python-is-python2 pkg-config libv8-dev libncurses5-dev libncursesw5-dev \
       postgresql-server-dev-14 build-essential

RUN curl https://bootstrap.pypa.io/pip/2.7/get-pip.py --output get-pip.py \
    && python2 get-pip.py
