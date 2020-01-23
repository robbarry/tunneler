# ssher

Use this tool to connect to MongoDB on DATA1 (eventually, could be repurposed for all WSJ data team db connections).

## Installation instructions

### 1. Tell Rob that you need to access Mongo

### 2. Add your DJ username to your `bash` profile:

	echo "export DJ_USERNAME=[YOUR_USERNAME]" >> ~/.profile && source ~/.profile

### 3. Install Docker

	sudo apt-get install docker.io

#### 3(a). If necessary, add your user to the Docker group (you'll need to reconnect):

	sudo usermod -aG docker [USERNAME]

### 4. Clone repository

	git clone git@github.com:robbarry/ssher.git

### 5. Build container

	cd ssher && ./build

### To stop/start the container, run:

	docker container [stop/start] mongodb

## Todo

* Unjankify the build params so multiple dynamic instances can be launched