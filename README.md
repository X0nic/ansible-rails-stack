Ansible Rails Stack
===================

 Heavily based off of [Mazer Rackham](https://github.com/jlund/mazer-rackham)

 Sample [Ansible](http://www.ansibleworks.com/) Playbook for Rack applications that installs Nginx, Passenger, and Ruby 2.0.0 (or 1.9.3). It also demonstrates how to deploy a [basic Rack application](https://github.com/jlund/imgur-display) from a git repository.

 Specifically, it does the following:

 * Upgrades packages
 * Installs a few crucial programs like git, NTP, and Vim
 * Creates a deploy user that the application files will belong to
 * Adds an SSH public key to the deploy user's Authorized Keys file
 * Reconfigures OpenSSH to only allow access via SSH keys
 * Installs Ruby 2.0.0 (or 1.9.3)
 * Installs Bundler
 * Installs Nginx + Passenger
 * Sets up and enables an Nginx vhost
 * Creates all necessary application directories
 * Uses git to checkout the latest revision of the [Blank Rails App](https://github.com/X0nic/blank-rails-app) codebase
 * Creates required symlinks
 * Uses bundler to install all Gem dependencies

Running this playbook will leave you with a fully-functional blank rails app. Thanks to [Joshua Lund](https://github.com/jlund) for [Mazer Rackham](https://github.com/jlund/mazer-rackham)

This playbook will run on Ubuntu 12.04 LTS and higher, and also works on Debian 7.

Enjoy!

Testing this playbook with Vagrant
----------------------------------

* Install Ansible
  * This playbook frequently uses new Ansible features, so installing the development version is recommended
* Download and install [Vagrant](http://vagrantup.com/)
* Copy or rename `Vagrantfile.example` to `Vagrantfile`
* Copy or rename `ansible_hosts.example` to `ansible_hosts`
* Comment out the `user: root` line from `rails-setup.yml` and uncomment
  the two lines below `Vagrant setup`
* Run `vagrant up` in a terminal from within this folder
* When the Ansible provisioning completes, visit [http://localhost:8080/](localhost:8080)
  in your host machine's browser to view the running Rack app
* Run `vagrant halt` to shutdown the VM
* Run `vagrant destroy` to delete the VM's data
