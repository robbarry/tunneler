# tunneler

Use this tool for easy port forwarding.

## Installation instructions

These instructions are for use on Linux.

### 1. Clone the repo

	git clone git@github.com:robbarry/tunneler.git
	cd tunneler

### 2. (optional) Add SSH keys

If you've already got SSH keys you want to use, copy them to the `certs`. Call your private key `tunneler_rsa` and your public key `tunneler_rsa.pub`.

If you don't add your own SSH keys, the setup script will create them for you.

### 3. Run setup

#### On Linux:

One stop shop! Just run:

	./setup

#### On a Mac:

Install Docker and related components:

	brew install docker docker-machine
	brew cask install virtualbox
	docker-machine create --driver virtualbox default
	docker-machine env default
	eval "$(docker-machine env default)"

Build the container:

	./build

#### On a PC:	

TBD.

### 4. Share the auto-generated SSH key with server admin

If you let the setup auto create your SSH keys, share the public key with your server admin so they can associate it with your username.

### 5. Create the container

	./create [CONTAINER_NAME] [YOUR_USERNAME] [HOST_IP] [LOCAL_PORT] [REMOTE_PORT]

For example, if you wanted to connect to MongoDB on `192.168.0.5` port `27017` with the username `jsmith`, you would type:

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

You can also have the container [start automatically on boot](https://docs.docker.com/config/containers/start-containers-automatically/).
