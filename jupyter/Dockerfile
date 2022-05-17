FROM ubuntu:18.04

RUN apt update && \
	echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections && \
	apt install git mc python3-dev python3-pip -y && \
	pip3 install jupyter

ENV usual "noroot"
RUN useradd -m -d /home/${usual} ${usual} && \
	chown -R ${usual} /home/${usual} && \
	chmod -R 755 -R /home/${usual} && \
	chsh -s /bin/bash ${usual}
ADD jyputer.sh /home/${usual}
RUN chown ${usual} /home/${usual}/jyputer.sh && chmod +x /home/${usual}/jyputer.sh

USER ${usual}
WORKDIR /home/${usual}
RUN echo ${USER} && whoami && pwd

ENTRYPOINT ["/home/noroot/jyputer.sh"]

EXPOSE 10000

