export tag=v1.0
root:
	export ROOT=github.com/cncamp/golang

release:
	echo "building httpserver container"
	docker build -t cncamp/httpserver:${tag} .

push: release
	echo "pushing cncamp/httpserver"
	docker push cncamp/httpserver:v1.0
