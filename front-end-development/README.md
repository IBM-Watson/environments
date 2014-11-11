# Front-End Development Stack

[View on Vagrant Cloud](https://vagrantcloud.com/IBM-Watson/boxes/front-end)

Built on `ubuntu/trusty64`, this box adds `zsh` with [oh-my-zsh](https://github.com/robbyrussell/oh-my-zsh) (and a custom theme), Git 2.1.2, Ruby 2.0.0-p481 managed through [rbenv](http://rbenv.org/) with [Bundler](http://bundler.io/) installed, and Node 0.10.32 managed through [nvm](https://github.com/creationix/nvm) with [Yeoman](http://yeoman.io/), [Bower](http://bower.io/), [Gulp](http://gulpjs.com/), and [Style Prototypes](https://github.com/north/generator-style-prototype) installed and ready to use.

### Recommended Vagrantfile

When using this box, it's recommended you use `nfs`. If not, Node has a tendency to be cranky. Starting with the following for your Vagrantfile will set the following up for you:

* Sets up a private network for NFS and sets `/vagrant` (shared folder) to use NFS (will prompt you for your administrative password, remove on Windows machines)
* Copy your host's `.gitconfig` file into the Virtual Machine
* Sets `vagrant ssh` to use an interactive ZSH session instead of the standard non-interactive BASH session. This allows Node and Ruby commands to be piped in to the VM via `vagrant ssh -c` and allows interactive commands (like Yeoman prompts) to be used through SSH as well

During installation, you will be prompted for your host's admin password if you are setting up this Virtual Machine using NFS.

```ruby
# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "IBM-Watson/front-end"

  # Copy host gitconfig into the Virtual Machine
  # On Windows if not using Powershell, change `~/.gitconfig` to `C:\Users\$USER` with $USER being your user name
  config.vm.provision "file", source: "~/.gitconfig", destination: ".gitconfig"

  # Set the shell for SSH to be an interactive ZSH session
  config.ssh.shell = '/bin/zsh -i'

  # Set up Vagrant folder to be NFS and provide it a private network
  config.vm.synced_folder ".", "/vagrant", type: "nfs"
  config.vm.network :private_network, ip: '172.10.10.10'
end
```

If you get an error during `vagrant up` regarding not having the correct shell available, comment out the `config.ssh.shell` option and try again. Once the machine is up, uncomment that line.