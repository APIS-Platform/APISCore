APIS Core for Docker
================

[![Docker Stats](http://dockeri.co/image/apisplatform/apisj)](https://hub.docker.com/r/apisplatform/apisj/)

Docker image to run APIS Core node in a container.

Supports APIS Masternode & Mining & RPC


Recommended System Requirements
------------

* PC, cloud platform instance, or VPS with Ubuntu OS and Docker installed.
* Stable network with average speed of 400kbps
* Running Ubuntu 16.04 LTS or later
* Processor performance equivant to 1.5 vCore(Vultur)
* At least 2 GB of RAM
* At least 20 GB of storage to store the block chain files

Recommended VPS Products
------------

VPS Provider Name | Service Name | System Spec
---------|--------------|------------
Amazon Web Services (AWS) | t2.small (EC2) | 1 CPU / 2GB RAM
Microsoft Azure | D1 (Linux VM) | 1 Core / 3.5GB RAM / 50GB Storage
Google Cloud Platform | n1-standard-1 (Compute Engine) | 1 vCPU / 3.75GB RAM
Vultur | VC2 | 1 vCPU / 2048MB RAM

Pulling Docker Image
-----------------------

Anyone can pull APIS Core docker image for Ubuntu 16.04 LTS machines with this command :

    $ sudo docker pull apisplatform/apisj
    ...
    Status: Downloaded newer image for apisplatform/apisj:latest
After this step, you can create your own APIS Core docker container with downloaded image.

Setting Up Docker Data Volume & Starting Docker Container
-----------------------

You must set up docker data volume for apis wallet to keep your keystore & block data safely.<br />With following command, you can set your local data volume for keystore backup and start your container.

    $ cd ~
    $ mkdir apisData
    $ sudo docker run --net=host -it --name apisj -v ~/apisData:/apis/apisData apisplatform/apisj /bin/bash
    ...
    root@abcdef012345:/#
Now, you can access into APIS Core docker container with your bash shell.

Setting Up APIS Core
-----------

1. Run `apis-core` script with `sh` command

        root@abcdef012345:/# sh ./apis-core

2. Set mining config (We recommend to load private key from PC wallet)

        You can get rewards through APIS Block mining.
        You should input Private key of a miner to start mining.
        The chance of getting reward goes higher with the registered miner's balance.
        --
        No Private key is found.
        --
        1. Generate a new Private key
        2. Input your Private key
        3. Exit
        >> 2

        Please input your Private key.
        >> d4e68558977bc0aaaaeced983c574bffd0e2d98123a7a687adbba58c8fbfffff

        Please input your password : 
        Please confirm your password : 
        Please input alias : testMiner

3. Load locked private key and unlock it to run mining

        1. Generate a new Private key
        2. Import your Private key
        3. Select coinbase from locked Private key file
        4. Deactivate mining function
        5. Exit
        >> 3
        Which address would you like to mining and enable mining?
        [1] ff275aa2cc4661ec61145089331b3666d781a348
        >> 1
        Please enter the password of [ff275aa2cc4661ec61145089331b3666d781a348]
        >>
        Mining is enabled and saved to settings.
      After this step, you will be automatically switched to masternode setup.


4. Set masternode config (We recommend to load private key from PC wallet with enough balance and mineral)

        You should input Private key of a masternode.
        The balance of the Masternode must be exactly 50,000, 200,000, and 500,000 APIS.
        --
        1. Generate a new Private key
        2. Import your Private key
        3. Select Masternode from locked Private key and enable masternode
        4. Deactivate Masternode function
        5. Exit
        >>
      Setting masternode will be as same as we described before.<br>Be sure to register appropriate wallet! Or masternode will not start!

        Please enter the address to receive the Masternode's reward instead.
        >> AAAAA....12345
      And you should enter reward wallet in this step.

5. Set RPC options if you want.

        The current setting is as follows.

        use_rpc             : null
        port                : null
        id                  : null
        password            : null
        max_connections     : null
        allow_ip            : null

        Do you want to change the settings?
        0. Disable RPC server
        1. Enable RPC server with this setting
        2. Change port
        3. Change id
        4. Change password
        5. Change max_connections
        6. Change allow_ip
        7. Exit
        >>

See APIS Core running
-------------

    20:45:27.428 INFO  [ApisFactory.java:62]	  Starting APIS...
    20:45:29.421 INFO  [Initializer.java:49]	  Running apis-mainnet.json, core version: ...
    ...

Credits
-------

APIS Team
