# docker run -d -v /etc/localtime:/etc/localtime:ro -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY  --name intellij silanpa/intellij

FROM debian:sid
MAINTAINER Victor Silanpa<silanpadev@gmail.com>

RUN	apt-get update && apt-get install -y \
    tar \
    wget \
	&& rm -rf /var/lib/apt/lists/* 

ENV HOME /home/intellij

RUN useradd --create-home --home-dir $HOME intellij \
	&& gpasswd -a intellij root \
	&& chown -R intellij:intellij $HOME

RUN wget https://download.jetbrains.com/idea/ideaIU-2016.2.5.tar.gz -P /home/intellij/download; tar zxvf /home/intellij/download/ideaIU-2016.2.5.tar.gz

WORKDIR $HOME/download/ideaIU-2016.2.5/bin

ADD ./idea /usr/sbin/intellij
RUN chmod +x /usr/sbin/intellij

USER intellij

CMD /usr/sbin/intellij



