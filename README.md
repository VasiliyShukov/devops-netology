Задание 2  
		sudo docker version && docker compose version  
		Client: Docker Engine - Community  
		 Version:           25.0.3  
		 API version:       1.44  
		 Go version:        go1.21.6  
		 Git commit:        4debf41  
		 Built:             Tue Feb  6 21:14:17 2024  
		 OS/Arch:           linux/amd64  
		 Context:           default  
  
Server: Docker Engine - Community  
 Engine:  
  Version:          25.0.3  
  API version:      1.44 (minimum version 1.24)  
  Go version:       go1.21.6  
  Git commit:       f417435  
  Built:            Tue Feb  6 21:14:17 2024  
  OS/Arch:          linux/amd64  
  Experimental:     false  
 containerd:  
  Version:          1.6.28  
  GitCommit:        ae07eda36dd25f8a1b98dfbf587313b99c0190bb  
 runc:  
  Version:          1.1.12  
  GitCommit:        v1.1.12-0-g51d5e94  
 docker-init:  
  Version:          0.19.0  
  GitCommit:        de40ad0  
Docker Compose version v2.24.5  
  
Задание 3  
Билд заканчивается удалением диска, почему ?  
  Пример hcl  
	build {  
	  sources = ["source.yandex.debian_docker"]  
  
	  provisioner "shell" {  
		inline = ["echo 'hello from packer'"]  
	  }  
  
	}  
vagrant@server1:/vagrant$ packer build mydebian.json.pkr.hcl  
yandex.debian_docker: output will be in this color.  
  
==> yandex.debian_docker: Creating temporary RSA SSH key for instance...  
==> yandex.debian_docker: Using as source image: fd8tg1k... (name: "debian-11-v20240212", family: "debian-11")  
==> yandex.debian_docker: Use provided subnet id e9b73ud1...  
==> yandex.debian_docker: Creating disk...  
==> yandex.debian_docker: Creating instance...  
==> yandex.debian_docker: Waiting for instance with id fhmnpkjf2... to become active...  
    yandex.debian_docker: Detected instance IP: 158.160.48.94  
==> yandex.debian_docker: Using SSH communicator to connect: 158.160.48.94  
==> yandex.debian_docker: Waiting for SSH to become available...  
==> yandex.debian_docker: Connected to SSH!  
==> yandex.debian_docker: Provisioning with shell script: /tmp/packer-shell1931808343  
    yandex.debian_docker: hello from packer  
==> yandex.debian_docker: Stopping instance...  
==> yandex.debian_docker: Deleting instance...  
    yandex.debian_docker: Instance has been deleted!  
==> yandex.debian_docker: Creating image: debian-11-docker  
==> yandex.debian_docker: Waiting for image to complete...  
==> yandex.debian_docker: Success image create...  
==> yandex.debian_docker: Destroying boot disk...  
    yandex.debian_docker: Disk has been deleted!  
Build 'yandex.debian_docker' finished after 2 minutes 16 seconds.  
