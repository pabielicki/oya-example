# Oya usage example

This is a sample Rails application to demononstrate Oya usage.
We will init oya, import docker, circleci packages and generate config files fot them.

## Init
Init creates Oyafile in project repository

  $ oya init
  
## Packs
Pack is a set of tasks.
First we need to fetch package with `oya get` command.

  $ oya get github.com/tooploox/oya-packs
 
Than add Import to Oyafile

```
Project: project
Import:
 docker: github.com/tooploox/oya-packs/docker
 circleci: github.com/tooploox/oya-packs/circleci
```
 
## Pack tasks
When packs are fetched and Imported in our project we can run tasks from packs.
Docker and CircleCi implements generate task. Which copies sample configs.

  $ oya run docker.generate
  $ oya run circleci.generate

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

## Tasks

