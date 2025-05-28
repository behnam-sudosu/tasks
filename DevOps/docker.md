# docker
## install docker
	in Iran we are sanction
	use vpn
	use shekan site
	bogzar site
	403.online site
	unlink /etc/resolv.conf
	touch /etc/resolv.conf
		nameserver 185.206.92.250
		nameserver 185.231.181.206
	install docker 22.4 ===>> go to docker site
	first uninstall last version
		for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
	sudo apt-get update
	sudo apt-get install ca-certificates curl
	sudo install -m 0755 -d /etc/apt/keyrings
	sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
	sudo chmod a+r /etc/apt/keyrings/docker.asc
	echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null	
	sudo apt-get update
	sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
	
	
	docker-ce ===>> docker comminty edition
	docker-ee ===>> docker enterprise edition
		
	systemctl status docker.service
	systemctl enable docker.service
	docker --version
	docker ===>> show all switch and help
		docker commands ===>> show commands
		management commands ===>> manage
		swarm commands ===>>
	docker volume ===>> show command for volume
	
	
	ls /var/lib/docker ===>> all file save here
	must mount this directory to another disk
	
## command
	docker countainer
	docker image
	docker network
	docker volume
	
	docker login ===>> outomaticly connect to docker hub
		username
		password
	docker logout ===>> go outside
	
	docker pull hello-world ===>> download image (lates image)
	docker images ===>> show all images you pulled
	docker pull ubuntu:22.04 (you shouldn't pull latest in production)
	docker run ubuntu:22.04 or ===>> run countainer image
	docker countainer run ubuntu:22.04
	docker ps ===>> show docker countainer image run
	docker ps -a ===>> show all docker countainer
	docker run -it ubuntu:22.04 /bin/bash ===>> i = interactive, t = tty
	
	CTRL + d ===>> exit countainer