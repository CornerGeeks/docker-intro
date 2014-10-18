# Some Dockerfiles for learning
# 



#################################################
# apache
#################################################
- Build image from Dockerfile

	cd apache 
	docker build -t devfest/apache .
	cd ..

- Build image from Dockerfile

	docker run -d -p 8000:80 -v "`pwd`/www":/var/www/html devfest/apache 

#################################################
# mysql
#################################################
- Using https://registry.hub.docker.com/_/mysql/
- Start MySQL container with a name and password

	docker run --name mysqlserver -e MYSQL_ROOT_PASSWORD=password -d mysql

- Start Apache container (specified above) and link to this MySQL container
- Test with localhost:8000/mysq.php

	docker run -d --link mysqlserver:db -p 8000:80 -v "`pwd`/www":/var/www/html devfest/apache 


#################################################
# bepsoke slides : self contained slide deck
# similar to application deployment
#################################################
- Build image from Dockerfile

	cd bespoke
	docker build -t devfest/bespoke .
	cd ..

- Build image from Dockerfile

	docker run -p 8080:8080 -p 35729:35729 devfest/bespoke

#################################################
# node : Flow for provisioning your own container
#################################################
- Build image from Dockerfile

	cd node
	docker build -t devfest/node .
	cd ..


- Go back to root directory and map slides to /slides

	docker run -ti -p 8080:8080 -p 35729:35729 -v "`pwd`/slides":/slides devfest/node bash


-In container. Clone repo, get dependencies and run

	cd /slides
	git clone https://github.com/markdalgleish/presentation-tabs.git .
	npm install
	bower install
	gulp serve
