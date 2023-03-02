
### Quick Start:

   
1. ***Without local persistance*** : Default command for launching openproject from docker image:  
    ```
	docker run -it -p 8080:80 \  
		-e OPENPROJECT_SECRET_KEY_BASE=secret \  
		-e OPENPROJECT_HOST__NAME=localhost:8080 \  
		-e OPENPROJECT_HTTPS=false \  
		openproject/community:12
	```
2. **With Local persistance**

	1. Create the required directories for web app static and postgres db:  
	```
	sudo mkdir -p /home/mak/MEGA/MEGAsync/mak/openproject/{pgdata,assets}
	```
	2. Run the container with local volumes of pgdata and static for **persistence**:  
	```
	sudo docker run -d -p 8080:80 --name openproject \ 
	-e OPENPROJECT_SECRET_KEY_BASE=secret \  
	-e OPENPROJECT_HOST__NAME=localhost:8080 \  
	-e OPENPROJECT_HTTPS=false \ 
	-v /home/mak/MEGA/MEGAsync/mak/openproject/pgdata:/var/openproject/pgdata \  
	-v /home/mak/MEGA/MEGAsync/mak/openproject/assets:/var/openproject/assets \  
	openproject/community:12
	
	```  
3. You can then launch a browser and access your new OpenProject installation at `http://localhost:8080`. Easy!
4. To Stop the openproject container:  
	```
	docker stop openproject  
	```
5. To Start the openproject container:  
	```
	docker start openproject  
	```
6. To remove openproject
	```
	docker rm openproject  
	```
7. To See Logs:  
	```
	sudo docker logs -f --tail 1000 openproject  
	```