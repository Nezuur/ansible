# This is a decription of the Lab 10 module's tasks.
____

## **docker.yml** 
contains ansible playbook with test task of running "Hello_World" docker container on remote host.

## **mysql.yml**  
contains ansible playbook, which make an installation MySQL server with dependencies (python3-pymysql, libmysqlclient-dev), and then it'll make sure the service starts and change root password unsafety =)

## **user.yml**  
contains ansible playbook, that will create user and generate 2048bit key for it, after that keys will be downloaded to master host.

## **userc.yml** 
needs some preparation before. To transfer SSH key encrypted you have to do:
  - generate key pair (ssh-keygen -b 2048 -t rsa)
  - encrypt pub key with ansible vault (ansible-vault encrypt /dest/ssh/key.pub)
  - run playnook with vault key (ansible-playbook userc.yml --ask-vault-pass)
than it'll create user on remote host, esure that SSH directory is exist, and after that transfer encrypted key to r.host while decrypting it.

## **postfix.yml** 
An example of how tag works.
  - ansible-playbook postfix.yml --tags init (Will install apk postfix)
  - ansible-playbook postfix.yml --tags drop (Will uninstall apk postfix)
