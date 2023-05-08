FROM debian
RUN apt-get update && apt-get install --yes wget libasound2-dev xvfb xterm gettext-base
RUN dpkg --add-architecture i386 && apt update && apt-get install --yes wine32
WORKDIR /src
ENV WINEPREFIX /src/.wine
ADD wine.tar .
ARG target=".wine/drive_c/VARA FM/VARAFM.ini"
ADD ./VARAFM.ini ${target}
ADD ./VARA.ini .wine/drive_c/VARA/VARA.ini
RUN chown root:root -R /src/.wine
ADD asoundrc.subst .
