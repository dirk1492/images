all: push

TAG ?= 0.6
PREFIX ?= dil001/ubuntu-slim-arm64
BUILD_IMAGE ?= ubuntu-build
TAR_FILE ?= rootfs.tar

container: clean
	docker build -t $(BUILD_IMAGE) -f Dockerfile.build .
	docker create --name $(BUILD_IMAGE) $(BUILD_IMAGE)
	docker export $(BUILD_IMAGE) > $(TAR_FILE)
	docker build -t $(PREFIX):$(TAG) .
	docker tag $(PREFIX):$(TAG) $(PREFIX)

push: container
	docker push $(PREFIX):$(TAG)
	docker push $(PREFIX)

clean:
	docker rmi -f $(PREFIX):$(TAG) || true
	docker rmi -f $(PREFIX) || true
	docker rmi -f $(BUILD_IMAGE)   || true
	docker rm  -f $(BUILD_IMAGE)   || true
	rm -f $(TAR_FILE)
