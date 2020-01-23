# ssher

Use this tool to connect to MongoDB on Data1 (eventually, could be repurposed for all WSJ data team db connections).

## Installation instructions

1. Install Docker:

	sudo apt-get install docker

2. Clone instance:

	git clone git@github.com:robbarry/ssher.git

3. Build Container:

	cd ssher
	./build

4. Run container:

	./run

## Todo

* Unjankify the build params so multiple dynamic instances can be launched