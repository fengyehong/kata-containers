# Copyright (c) 2019-2022 Alibaba Cloud. All rights reserved.
# Copyright (c) 2019-2022 Ant Group. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

include ../../utils.mk

ifeq ($(ARCH), s390x)
default build check test clippy:
	@echo "s390x not support currently"
	exit 0
else

default: build

build:
	@echo "INFO: cargo build..."
	cargo build --all-features --target $(TRIPLE)

check: clippy format

clippy:
	@echo "INFO: cargo clippy..."
	cargo clippy --all-targets --all-features \
		-- \
		-D warnings

vendor:
	@echo "INFO: vendor do nothing.."

format:
	@echo "INFO: cargo fmt..."
	cargo fmt -- --check

clean:
	cargo clean

test:
ifdef SUPPORT_VIRTUALIZATION
	cargo test --all-features --target $(TRIPLE) -- --nocapture
else
	@echo "INFO: skip testing dragonball, it need virtualization support."
	exit 0
endif

endif # ifeq ($(ARCH), s390x)

.DEFAULT_GOAL := default
