# Sample Vagrantfile

1. **start**, learning vagrant from stracht
2. **swarm**, use vagrant for docker swarm

# Vagrant Command

1. Init vm: go to project dir and run `vagrant init`
2. Create vm: go to project dir contain Vagrantfile and run `vagrant up`
3. List vm: run `vagrant global-status`
4. SSHing into vm:
   1. go to project dir and run `vagrant ssh`
   2. run `vagrant ssh [vm-id]` from anywhere
5. Destroy vm:
   1. go to project dir and run `vagrant destroy`
   2. or run `vagrant destroy [vm-id]` from anywhere
6. Stop vm:
   1. go to project dir and run `vagrant halt`
   2. or run `vagrant halt [vm-id]` from anywhere
7. reload vm: `vagrant reload`
