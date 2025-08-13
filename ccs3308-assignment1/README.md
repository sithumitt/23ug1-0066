Deployment requirements are :  

Having a laptop with VMWare installed, and inside that, Ubuntu OS is installed. And a virtual Docker engine together with the Docker Compose plugin. To run the Flask application, a VM should also be installed with the Python application. At the moment assignment needs an internet connection to run and establish connections between the container applications.


Application Description 

This is a 2-service Docker application with a web service and a database service. For the web service, a Python Flask app serves a simple web page on port 5000. And for the database MySQL 8.0, storing the number of visits with persistent storage. And these 2 applications are communicating with each other and give a service of which application is built. The web service communicates with the database service to maintain state.

Network and volume details

The web and database containers are connected via the Docker network app-net with subnet 172.18.0.0/16. The web container uses IP 172.18.0.2 and the database container uses IP 172.18.0.3, allowing them to communicate easily. The database stores its files in the named volume db-data.

Network List 


Volume list 









IP Address of the 2 applications 



Container Configurations of containers 1 and 2 




The web container runs a Flask app on port 5000 and connects to the database using environment variables. The db container uses mysql:8.0, listens on port 3306, and stores data in the persistent volume db-data. Both containers are connected via the app-net network, allowing communication, and the web container is set to restart automatically if it fails.
Container list 

Instructions
Prepare, run, pause, and delete the application:
 Prepare application resources 
./prepare-app.sh
Start the application
./start-app.sh
The web app is available at http://localhost:5000. Open the web browser and type this,s then it will show the visiting count.
Pause/stop the application (preserves persistent data)
./stop-app.sh
Delete all application resources (containers, images, network, volumes)
./remove-app.sh



Assessment process record.
First, updated the sudo apt update
Then installed the dependencies: sudo apt install -y ca-certificates curl gnupg git
Then added Docker's official GPG key: sudo install -m 0755 -d /etc/apt/keyrings
Then install Docker Engine with  Compose plugin: sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
Then let My  user run Docker without sudo: sudo usermod -aG docker "$USER" newgrp docker
Then verified all my installations: docker --version, docker compose version, git --version
After that, create project folders and files, and paste relevant code inside them

Then perform the Prepare, run, pause, and delete operations, and upload the folder to the git hub under my registration number.




