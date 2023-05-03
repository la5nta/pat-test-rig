ARG FREEDATA_BRANCH=AGWPE

FROM debian
RUN apt-get update && apt-get install --yes wget git build-essential cmake python3 portaudio19-dev python3-pyaudio python3-pip python3-colorama python3-venv

WORKDIR /src
RUN git clone https://github.com/drowe67/codec2.git && cd codec2 && mkdir build_linux && cd build_linux && cmake .. && make
RUN git clone https://github.com/DJ2LS/FreeDATA.git
RUN ln -s /src/codec2 /src/FreeDATA/tnc/lib/codec2

ARG FREEDATA_BRANCH
RUN cd FreeDATA && git checkout $FREEDATA_BRANCH

# Hack because create_python_env.sh assumes python is installed into /bin/
RUN ln -s /usr/bin/python* /bin/
RUN cd /src/FreeDATA && ./tools/create_python_env.sh

WORKDIR /src/FreeDATA/tnc
ENTRYPOINT /bin/sh -c ". ../.venv/bin/activate && ./main.py --tx $DEVNAME --rx $DEVNAME --agwpe --agwpe-ip 0.0.0.0 --agwpe-port 8000"
