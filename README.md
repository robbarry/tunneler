# tunneler

Use this tool for easy port forwarding.

## Installation instructions

### 1. Clone the repo

	git clone git@github.com:robbarry/tunneler.git

### 2. Run setup

	cd tunneler
	./setup

### 3. Share the auto-generated SSH key with server admin
	
### 4. Create the container

	./create [CONTAINER_NAME] [YOUR_USERNAME] [HOST_IP] [LOCAL_PORT] [REMOTE_PORT]

For example, if you wanted to connect to MongoDB on `192.168.0.5` port `27017` with the username `jsmith`, you could type:

	./create mongodb jsmith 102.168.0.5 27017 27017

At which point `localhost:27017` would be bound to `192.168.0.5`'s port `27017`.

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
