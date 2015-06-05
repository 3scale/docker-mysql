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

push:
	docker push $(IMAGE)
