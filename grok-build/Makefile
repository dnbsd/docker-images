IMAGE ?= grok-build
TAG ?= latest
CONTAINER ?= grok-$(shell basename $(PWD))

.PHONY: all
all:
	@echo "make <build|create|start|clean>"

.PHONY: build
build:
	container build -t $(IMAGE):$(TAG) .

.PHONY: run
run:
	container run -i -t \
		--mount type=bind,source=$(HOME)/.grok,target=/home/grok/.grok \
		--mount type=bind,source=$(PWD),target=/workspace \
		--name $(CONTAINER) \
		--env TERM=$(TERM) \
		--interactive \
		--tty \
		--rm \
		$(IMAGE):$(TAG)

.PHONY: clean
clean:
	container image rm $(IMAGE):$(TAG)
