# docker run -d -v /etc/localtime:/etc/localtime:ro -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY --device /dev/snd:/dev/snd --name lastfm silanpa/lastfm


FROM debian:sid
MAINTAINER Victor Silanpa<silanpadev@gmail.com>

RUN	apt-get update && apt-get install -y \
	wget \
	gconf2 \
 	libasound2 \ 
	libgpod4 \
	libmad0 \
	libqt4-network \
	libqt4-sql \
	libqt4-xml \
	libqtcore4 \
	libqtgui4 \
	libx11-6 \
	alsa-utils \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/* 

ENV HOME /home/lastfm

RUN useradd --create-home --home-dir $HOME lastfm \
	&& gpasswd -a lastfm audio \
	&& chown -R lastfm:lastfm $HOME 

RUN wget security.ubuntu.com/ubuntu/pool/universe/l/lastfm/lastfm_1.5.4.27091+dfsg1-1ubuntu1_amd64.deb -P /home/lastfm/download 

RUN dpkg -i /home/lastfm/download/lastfm_1.5.4.27091+dfsg1-1ubuntu1_amd64.deb

WORKDIR $HOME
USER lastfm

ENTRYPOINT	[ "lastfm" ]
