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
