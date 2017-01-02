all: push

# 0.0.0 shouldn't clobber any released builds
TAG = 0.5
PREFIX = dil001/haproxy-arm64
HAPROXY_IMAGE = haproxy

container:
	docker build -t $(PREFIX):$(TAG) .

push: container
	docker push $(PREFIX):$(TAG)

clean:
	# remove haproxy images
	docker rmi -f $(PREFIX):$(TAG) || true
