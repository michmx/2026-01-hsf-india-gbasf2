# Setting up gbasf2 

```{warning}
Before getting started, make sure you understand the following:

* The GRID is NOT a local computing system like KEKCC.

* Once you submit jobs, they will be assigned to computing systems around the world.

* If your job is problematic, it will be distributed to the world and many sites will be affected.

Remember to always test your jobs locally before submitting to the grid!
```

## Setting up the environment

Gbasf2 is conveniently deployed via CVMFS. 

Unfortunately, **basf2 and gbasf2 environments are NOT compatible**. We will run gbasf2 in a new shell.

Every time you open a new terminal, you need to set up the environment by running the following command:

```bash
source /cvmfs/belle.kek.jp/grid/gbasf2/production/bashrc 
```

It will request your certificate passphrase the first time you run it in a terminal session. If everything is fine, 
you will see something like this:

```bash
~$ source /cvmfs/belle.kek.jp/grid/gbasf2/production/bashrc -g belle

gb2_proxy_init -g belle
Generating proxy...
Enter Certificate password: ********

Contacting CS...
Checking DN /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist
Username is user
Creating proxy for user@belle (/DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist)
Added VOMS attribute /belle
Uploading proxy..
Uploading /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist proxy to ProxyManager...
Loading user proxy
Uploading proxy on-the-fly
Cert file /home/user/.globus/usercert.pem
Key file  /home/user/.globus/userkey.pem
Loading cert and key
User credentials loaded
 Uploading...
Proxy uploaded
Proxy generated:
subject      : /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist/CN=9390450188/CN=2797830755
issuer       : /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist/CN=9390450188
identity     : /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist
timeleft     : 23:53:57
DIRAC group  : belle
path         : /tmp/x509up_u10076
username     : user
properties   : NormalUser
VOMS         : True
VOMS fqan    : ['/belle']

Proxies uploaded:
 DN                                                                                            | Until (GMT)
 /DC=ch/DC=cern/OU=Organic Units/OU=Users/CN=awesomeuser/CN=816860/CN=An Awesome Physicist | 2027/01/20 20:17
Succeed with return value:
0.0 
```

Be careful with warnings or error messages, there should be none.

```{note}
The proxy generated above is valid for 24 hours. If you keep your terminal open for more than 24 hours, you need to re-run the `source /cvmfs/belle.kek.jp/grid/gbasf2/production/bashrc` command to renew your proxy.
```

### Starting a proxy with a different group

If you are part of a group other than the default `belle`, you can specify the group with the `-g` option:

```bash
source /cvmfs/belle.kek.jp/grid/gbasf2/production/bashrc -g belle_starterkit
```

### Checking your proxy

You can check your proxy information with the following command:

```bash
gb2_proxy_info
```

It will show you information about your proxy, including the subject, issuer, identity, time left, DIRAC group, and VOMS attributes.


### Full local installation 

If you want to install gbasf2 locally without using CVMFS, you can follow the instructions in the [gbasf2 documentation](https://gbasf2.belle2.org/gbasf2install.html).

The only reason to do this is if you are interested in developing new features for gbasf2 itself. For analysis purposes, the CVMFS setup is sufficient and recommended.

```{note}
Interested on a new feature? Fantastic! 

Please contact comp-dirac-devel@belle2.org before starting any development to coordinate efforts.
```