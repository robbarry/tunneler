# ssher

Use this tool to connect to MongoDB on Data1 (eventually, could be repurposed for all WSJ data team db connections).

## Installation instructions

### 1. Send Rob a copy of your public key

This file should be located at:

	~/.ssh/id_rsa.pub

### 2. Add your username to your `bash` profile:

	echo "export DJ_USERNAME=YOUR_USERNAME" >> ~/.profile && source ~/.profile

### 3. Install Docker

	sudo apt-get install docker

### 4. Clone repository

	git clone git@github.com:robbarry/ssher.git

### 5. Build container

	cd ssher
	./build

### 6. Run container

	./run

## Todo

* Unjankify the build params so multiple dynamic instances can be launched