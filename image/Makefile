server_version=6.3.13

base_image=seafileltd/base:18.04
base_image_squashed=seafileltd/base:18.04-squashed
pro_base_image=seafileltd/pro-base:18.04
pro_base_image_squashed=seafileltd/pro-base:18.04-squashed
server_image=seafileltd/seafile:$(server_version)
server_image_squashed=seafileltd/seafile:$(server_version)-squashed
pro_server_image=seafileltd/seafile-pro:$(server_version)
pro_server_image_squashed=seafileltd/seafile-pro:$(server_version)-squashed
latest_pro_server_image=seafileltd/seafile-pro:latest
latest_server_image=seafileltd/seafile:latest

all:
	@echo
	@echo Pleaes use '"make base"' or '"make server"' or '"make push"'.
	@echo

base:
	cd base && docker build -t $(base_image) .

server:
	cd seafile && cp -rf ../../scripts ./ && docker build -t $(server_image) .

pro-base:
	cd pro_base && docker build -t $(pro_base_image) .

pro-server:
	cd pro_seafile && cp -rf ../../scripts ./ && docker build -t $(pro_server_image) .

push-base:
	docker push $(base_image)

push-pro-base:
	docker tag $(pro_base_image) ${host}/$(pro_base_image)
	docker push ${host}/$(pro_base_image)

push-server:
	docker push $(server_image)
	docker push $(latest_server_image)

push-pro-server:
	docker tag $(pro_server_image) ${host}/$(pro_server_image)
	docker tag $(pro_server_image) ${host}/$(latest_pro_server_image)
	docker push ${host}/$(pro_server_image)
	docker push ${host}/$(latest_pro_server_image)

push: push-base push-server

.PHONY: base server push push-base push-server
