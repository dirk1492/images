all: serve_hostname container

TAG = v1.4
PREFIX = dil001

serve_hostname: serve_hostname.go
	CGO_ENABLED=0 GOARCH=arm64 go build -a -installsuffix cgo --ldflags '-w' ./serve_hostname.go

container: serve_hostname
	docker build -t $(PREFIX)/serve_hostname-arm64:$(TAG) .
	docker tag $(PREFIX)/serve_hostname-arm64:$(TAG) $(PREFIX)/serve_hostname-arm64
	if [ -n "$(TEST_PREFIX)" ]; then \
	    docker tag -f $(PREFIX)/serve_hostname-arm64:$(TAG) $(TEST_PREFIX)/serve_hostname:$(TAG); \
	fi

push:
	docker push $(PREFIX)/serve_hostname-arm64:$(TAG)
	docker push $(PREFIX)/serve_hostname-arm64

	if [ -n "$(TEST_PREFIX)" ]; then \
	    docker push $(TEST_PREFIX)/serve_hostname-arm64:$(TAG); \
	fi

clean:
	rm -f serve_hostname
