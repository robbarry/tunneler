# ssher

Use this tool to connect to MongoDB on DATA1 (eventually, could be repurposed for all WSJ data team db connections).

## Installation instructions

### 1. Install Docker

	sudo apt-get install docker.io

If necessary, add your user to the Docker group (you'll need to reconnect):

	sudo usermod -aG docker [USERNAME]

### 2. Clone repository

	git clone git@github.com:robbarry/ssher.git

### 3. Build container

You'll need to specify the IP address of the machine you want to connect to.

	cd ssher && ./build [SERVER_IP_ADDRESS]

### 4. The build process will output an SSH key, which you'll need to share with the server administrator.

For example, see the SSH key below:

	Step 9/10 : CMD ["./entrypoint"]
	 ---> Running in 20553fe83aa2
	Removing intermediate container 20553fe83aa2
	 ---> 1ebf678f52c6
	Step 10/10 : RUN output="$( echo SHARE THIS KEY WITH YOUR ADMIN: &&                cat /root/.ssh/id_rsa.pub)" && echo $output
	 ---> Running in dc1e6101d410
	SHARE THIS KEY WITH YOUR ADMIN: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC5oHWTv4s5vHWaqm5Xx8ovyG+bgOB0JCyrXnXErNq9wjnWhB3jGirSQTMGHj53p3hDWR+gV1Zgf8BJfwp4ODsuPpMnuMNyuUMWlItyKxQco8P8zi8sjJ3TfW2DNYf0QGEdkvFIMryejIoFoooDC3uUI0ofMRuyC2VPT+wOLmSOf2mgDL838XYis4Z2BC/nlVMqk+Xd792Jrgmw1deP4bT4Jb1KJC3VuZdk8mZNE7vOtQYciP5rGp3xgJPT1ZFPfIvf3GkKwQlF80B7+UsfcbRjGvUoR17EozzF+lp88xTCsDOsa51yh1ItVD4sysnJu8deqSpuEg6R1RwB/cfs9b0f root@936b3b6c4fa0
	Removing intermediate container dc1e6101d410
	 ---> cd074353ff52
	Successfully built cd074353ff52

### 5. Create the container

	./create [CONTAINER_NAME] [YOUR_USERNAME] [LOCAL_PORT] [REMOTE_PORT]

For example, if you wanted to connect to MongoDB on port `27017` with the username `jsmith`, you could type:

	./create mongodb jsmith 27017 27017

At which point `localhost:27017` would be bound to the remote machine's port `27017`.

## Starting and stopping the connection

Once you've created the container, you can easily stop and start it using the following commands:

	docker container stop [CONTAINER_NAME]
	docker container start [CONTAINER_NAME]

## Other features

To view your running containers, you can type:

	docker ps

If you want to see all containers (including those which aren't running), type:

	docker ps -a

You can also delete the container. If you do so while it's running, you'll need to specify the `--force` parameter:

	docker rm [CONTAINER_NAME] --force