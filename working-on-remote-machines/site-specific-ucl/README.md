# HEP cluster at UCL

# SSH
SSH gateways are:

`plus1.hep.ucl.ac.uk`
`plus2.hep.ucl.ac.uk`

You can connect to them using: 
`ssh your-username@plus1.hep.ucl.ac.uk`

After conneting to `plus1` or `plus2`, you can accesso to all UCL machines, including those in the batch farm. UCL LEGEND users are currently using as interactive machine `pc204`, which can be directly access from the gateways using:
`ssh pc204`

Here is an example of `.ssh/config` file:
```
Host plus1
    HostName plus1.hep.ucl.ac.uk
    User your-user-name
    ForwardX11 yes
    ForwardX11Trusted yes
  Host plus2
    HostName plus2.hep.ucl.ac.uk
    User your-user-name
    ForwardX11 yes
    ForwardX11Trusted yes
  Host pc204
    HostName pc204
    User your-user-name
    ProxyCommand ssh plus1 -W %h:22
    ForwardX11 yes
    ForwardX11Trusted yes
```

## Jupyter Notebooks

To work in jupyter notebooks you will first need to add the 
virtual environment using: `python -m ipykernel install --user --name=testenv`.

Now you can set up a jupyter notebook instance using:
`jupyter notebook --port=8880 --no-browser`
You should use a different number for the port so no one is using the same port. Any number between 
8000 and 9000 should work. 
In a seperate tab you will need to enter the command:
`ssh -N -L 8880:localhost:8888 pc204`
to set up port forwarding where the first number should be the same as the port in the previous command.
The second number is your local port. To access the jupyter notebook go to your web browser and navigate to 
http://localhost:8888/ where the number is the same as the second number above.

## load software

To be updated!

First log in to the server

`ssh pc204`

then navigate to the test env

`cd /unix/legend/testenv-v02`

You will then need to source the config file using:

`source setup.sh`

Navigate to a production cycle:

`cd ref-prod/master`

Finally make a shell within the virtual environment and load all the software using:

`testenv-bash.sh config.json`

(venv) should appear at the start of your command line.

To exit this and return to the normal shell simply type:
`deactivate`.