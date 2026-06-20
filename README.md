# self-hosted-ubuntu
self-hosted-ubuntu
# Create a folder under the drive root
$ mkdir actions-runner; cd actions-runnerCopied! # Download the latest runner package
$ Invoke-WebRequest -Uri https://github.com/actions/runner/releases/download/v2.335.1/actions-runner-win-x64-2.335.1.zip -OutFile actions-runner-win-x64-2.335.1.zip# Optional: Validate the hash
$ if((Get-FileHash -Path actions-runner-win-x64-2.335.1.zip -Algorithm SHA256).Hash.ToUpper() -ne 'eb65c95277af42bcf3778a799c41359d224ba2a67b4de26b7cea1729b09c803d'.ToUpper()){ throw 'Computed checksum did not match' }# Extract the installer
$ Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$PWD/actions-runner-win-x64-2.335.1.zip", "$PWD")

# Create the runner and start the configuration experience
$ ./config.cmd --url https://github.com/naveenkumaryeti/self-hosted-ubuntu --token B7F5UCDG26MGXPX6UVSJONDKG3LGY# Run it!
$ ./run.cmd

# Use this YAML in your workflow file for each job
runs-on: self-hosted
