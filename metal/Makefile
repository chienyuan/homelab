.POSIX:

env ?= "prod"

default: boot cluster

~/.ssh/id_ed25519:
	ssh-keygen -t ed25519 -f "$@"

boot: ~/.ssh/id_ed25519
	ansible-playbook \
		--inventory inventories/${env}.yml \
		-vvv \
		boot.yml

cluster:
	ansible-playbook \
		--inventory inventories/${env}.yml \
		-vvv \
		cluster.yml

shutdown:
	ansible-playbook \
		--inventory inventories/${env}.yml \
		shutdown.yml

vagrant:
	vagrant up
