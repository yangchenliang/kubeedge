
GO_LDFLAGS=-ldflags '$(shell ../hack/lib/version.sh)'
# make keadm
.PHONY: default keadm
keadm: verify 
	go build $(GO_LDFLAGS) -o keadm cmd/keadm/keadm.go

.PHONY: verify
verify:
	bash ../hack/verify-golang.sh

lint:
	golangci-lint run --deadline '10m' --disable-all -E golint ./...
	go vet ./...

.PHONY: clean
clean:
	$(RM) keadm

# .PHONY: cross_build
# cross_build:
# 	export GOARCH=arm
# 	export GOOS="linux"
# 	export GOARM=6
# 	export CGO_ENABLED=1
# 	export CC=arm-linux-gnueabi-gcc
# 	go build keadm.go -o keadm

