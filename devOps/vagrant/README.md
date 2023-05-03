# Sample Vagrantfile

1. **start**, learning vagrant from stracht
2. **swarm**, use vagrant for docker swarm

# Vagrant Command

1. Init vm: go to project dir and run `vagrant init`
2. Create vm: go to project dir contain Vagrantfile and run `vagrant up`
3. List vm: run `vagrant global-status`
4. SSHing into vm:
    a. go to project dir and run `vagrant ssh`
    b. run `vagrant ssh [vm-id]` from anywhere
5. Destroy vm:
    a. go to project dir and run `vagrant destroy`
    b. or run `vagrant destroy [vm-id]` from anywhere