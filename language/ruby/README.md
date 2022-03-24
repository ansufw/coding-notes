# install Ruby 

using ruby installation manager
- https://github.com/rbenv/rbenv
- https://github.com/rvm/rvm
- https://hixonrails.com/ruby-on-rails-tutorials/ruby-environment-management/

## via rbenv

- check only stable list `rbenv install -l`
- check all list available `rbenv install -L`



## via RVM

http://rvm.io/rvm/install

1. add gpg key 

```
gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

2. install rvm

```
curl -sSL https://get.rvm.io | bash -s stable
```

3. install Ruby version

```
rvm install 2.7.5 
```

4. check the list `rvm list`
5. let's make this more interesting by install another version `rvm insall 3.0.0`
6. again check the list 
7. see other commands available `rvm help`

