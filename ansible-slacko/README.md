ansible-slacko
==============

Prepare the environment:
------------------------

- clone the repo
`$ git clone https://github.com/fernandoravagnani/iaac`

- enter the repo directory:
`$ cd iaac/ansible-slacko`

- start the vagrant virtual machines
`/iaac/ansible-slacko$ vagrant up`

- enter the iaac machine
`/iaac/ansible-slacko$ vagrant ssh iaac`

- create the ssh keys that will be copied into the instances
`vagrant@iaac-station:~$ ssh-keygen -b 2048 -t rsa -f ~/.ssh/id_rsa -q -N ""`

- copy this public key to be pasted into the server instance
`vagrant@iaac-station:~$ cat ~/.ssh/id_rsa.pub`

- exit the iaac-station machine
`vagrant@iaac-station:~$ exit`

- enter the server machine
`/iaac/ansible-slacko$ vagrant ssh iaac`

- paste the public as a new line inside the authorized_keys
`vagrant@server:~$ vim ~/.ssh/authorized_keys`

- exit the server machine
`vagrant@server:~$ exit`

Execute the playbook:
---------------------

- enter the iaac machine
`/iaac/ansible-slacko$ vagrant ssh iaac`

- change the directory to /vagrant
`vagrant@iaac-station:~$ cd /vagrant`

- execute the playbook
`vagrant@iaac-station:/vagrant$ ansible-playbook -i inventory.yml --limit remoto playbook.yml`

- when finished, go to the web browser and enther the URL
`http://localhost:8000/healthcheck`