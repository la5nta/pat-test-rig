FROM debian
RUN apt-get update && apt-get install --yes wget unzip build-essential alsa-utils gettext-base

WORKDIR /src
RUN apt-get install --yes libqt5core5a libfftw3-dev libpulse-dev libqt5serialport5-dev libasound-dev
RUN wget https://www.cantab.net/users/john.wiseman/Downloads/Beta/QtSMSource.zip && unzip QtSMSource.zip
RUN qmake && make

WORKDIR /run
ADD QtSoundModem.ini.subst QtSoundModem.ini.subst
ENTRYPOINT /bin/sh -c "envsubst < QtSoundModem.ini.subst > QtSoundModem.ini; /src/QtSoundModem nogui"
