REGISTRY=quay.io
REPO=mysql
TAG=tmpfs-5.6
REPO_ROOT=$(REGISTRY)/3scale
IMAGE=$(REPO_ROOT)/$(REPO):$(TAG)
RUN:=docker run --cap-add=SYS_ADMIN

build:
	docker build -t $(IMAGE) --rm .
bash:
	$(RUN) -it --rm $(IMAGE) bash

release: build push

test: build
	- docker rm --force mysql_tmpfs_test 2> /dev/null
	$(RUN) -it --name mysql_tmpfs_test --detach $(IMAGE) sleep 10
	docker exec mysql_tmpfs_test /mysql/run

push:
	docker push $(IMAGE)
