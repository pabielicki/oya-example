# Oya usage example

This is a sample Rails application to demononstrate Oya usage.
We will init oya, import docker, circleci packages and generate config files fot them.

    $ oya init
    $ oya get github.com/bart84ek/oya-packs
    $ oya import github.com/bart84ek/oya-packs/docker
    $ oya run docker.generate
    
Dockerized! now we can :

    $ docker build -t example_app .
    $ docker run -it -p 80:3000 example_app
    
And app should be running on http://localhost/.


## Init
Init creates Oyafile in project repository

    $ oya init
  
## Packs
Pack is a set of tasks.
First we need to fetch package with `oya get` command. All packages will be stored in `.oya/vendor` directory

    $ oya get github.com/tooploox/oya-packs
 
Than we can import our pack.

    $ oya import github.com/tooploox/oya-packs/docker
    
Import adds Import statment in Oyafile. Pack is imported with alias (default last word from url).

```
Project: project
Import:
 docker: github.com/tooploox/oya-packs/docker
```
 
## Pack tasks
When packs are fetched and Imported in our project we can run tasks from packs.
Docker and CircleCi implements generate task. Which copies sample configs.

    $ oya run docker.generate
    $ oya run docker.build
    $ oya run docker.run
    $ oya run docker.stop
    

# Oyafile

Example:

```
Project: project
Import:
 docker: github.com/bart84ek/oya_packs/docker
 
Values:
  msg: Hello oya!
test: |
  echo $msg
  echo "Done"
```

