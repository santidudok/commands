# commands

# Create a folder

$ mkdir actions-runner && cd actions-runner# Download the latest runner package
$ curl -o actions-runner-linux-x64-2.300.2.tar.gz -L https://github.com/actions/runner/releases/download/v2.300.2/actions-runner-linux-x64-2.300.2.tar.gz# Optional: Validate the hash
$ echo "ed5bf2799c1ef7b2dd607df66e6b676dff8c44fb359c6fedc9ebf7db53339f0c  actions-runner-linux-x64-2.300.2.tar.gz" | shasum -a 256 -c# Extract the installer
$ tar xzf ./actions-runner-linux-x64-2.300.2.tar.gz

Configure

# Create the runner and start the configuration experience
$ ./config.sh --url https://github.com/individual-s6/PictureService --token ANTVETWZ3TWKW3NTZJHRTFTDX77TG# Last step, run it!
$ ./run.sh

Using your self-hosted runner

# Use this YAML in your workflow file for each job
runs-on: self-hosted




For docker image building it is required that docker is installed, this can be done via a new terminal:
sudo apt install apt-transport-https curl gnupg-agent ca-certificates software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
sudo apt install docker-ce docker-ce-cli containerd.io -y
Now that docker is installed it is worth adding the user to the docker group so that sudo is not needed for every docker command:
sudo usermod -aG docker $USER
newgrp docker
docker version
The last command should show the version of docker installed.
If the docker workflow has issue logging in to dockerhub, and its a permission issue, run the following command
sudo chmod 666 /var/run/docker.sock
FOR ALL SCRIPTS: any points on failure could be related to trying windows only actions despite the running being on ubuntu/linux so check the workflow files and consider that the issue may be caused by this. 
One fix: replace commands that are being run which would normally not work on linux with ones that do. Example: New-Item -> mkdir
