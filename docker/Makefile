ENV_FILE := $(CURDIR)/.env

include $(ENV_FILE)

.check-image:
	@if [ -z "$$(docker images -q $(IMAGE_NAME))" ]; then \
		echo "Image $(IMAGE_NAME) does not exist"; \
		make .build; \
	else \
		echo "$(IMAGE_NAME) already exists..."; \
	fi

.build:
	docker build -t $(IMAGE_NAME) .

run: .check-image
	docker-compose --env-file $(ENV_FILE) up