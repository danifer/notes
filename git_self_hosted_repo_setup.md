Setup self-hosted Git repository server with SSH keys and bare repository initialization.

Setup a new repository on a self-hosted Git server

  create repository on repo host (dfw2)
    mkdir /home/git/repositories/*.git

  initialize that repository (in the location you just created)
    git init --bare

  create a ssh key for the user that's going to access it
    As the remote accessing user:
      ssh-keygen -t rsa
        no password

  add that ssh public key to the git users's authorized keys on the repo host (dfw2)
    nano /home/git/.ssh/authorized_keys
