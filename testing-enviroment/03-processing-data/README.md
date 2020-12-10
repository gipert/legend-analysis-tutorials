# Processing the Data

## Creating a new Production Cycle

Before you start this tutorial make sure your cluster ssh key is linked to your [github](https://github.com/mmatteo/legend-analysis-tutorials/tree/main/testing-enviroment/01-ssh-tricks#adding-keys-to-github).

Starting in the test environment.

First you will need to source the config file as before with:

`source setup.sh`

Now navigate to `user-prod` and create a new production cycle using:

`testenv-init.sh -o mmatteo -b master 'whoami'-test-v01`

The apostrophe's on the whoami should be backwards quotation marks ``. 
This is a bash command that will give back your username. In the future you can change 'test' to whatever the goal of the production cycle will be. So the naming convention should be: `username-goalOfTheCycle-v01`.

You should now be able to find you new production cycle in the `user-prod`.

## Processing Data

Inide your new production cycle you can run the script:

`testenv-r2d.sh -m 100 config.json ../../ref-prod/master/data/meta/keylists/V04199A-th_HS2_lat_psa-all.txt`

to process the data in the reference production.
The number in the command (100 here) controls the number of waveforms to be processed. In the next tutorial we will go through how to customize your production. 