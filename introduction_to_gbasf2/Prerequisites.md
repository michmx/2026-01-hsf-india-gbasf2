# Prerequisites

You can look at the official [gbasf2 documentation](https://gbasf2.belle2.org/prerequisites.html).
Here we summarize the main points.

```note
Unfortunately, if you don’t have a grid certificate, you will only be able to observe today.
```

## Grid certificate

Make sure you have a valid grid certificate, issued within one year

For India, you can get one at https://ca.garudaindia.in/

Once available, the certificate must be installed in `~/.globus` and on the web browser.

In the terminal 

```bash
ls -l ~/.globus

-rw-r--r--. 1 myuser 3.5K Dec 10 15:41 usercert.pem
-r--------. 1 myuser 2.0K Dec 10 15:41 userkey.pem
```

```{warning}
Private means private! Make sure no one else can read your private key (`userkey.pem`).
```

And for the web browser, the following links may be useful 

* Windows: https://www.sdcc.bnl.gov/information/getting-started/certificate-key-management-windows
* Mac: https://www.sdcc.bnl.gov/information/certificate-and-key-management-macos
* Firefox (Linux/Windows/Mac): 
  - Click Preferences (or Options) 
  - click Advanced 
  - click the Encryption tab 
  - click View Certificates 
  - and then click the Your Certificates tab

If you have any issues, please contact your local IT support team.

## VO membership 

Your membership on the Belle VO must be active or renewed within a year.
Access [the Belle VO page](https://voms.cc.kek.jp:8443/voms/belle) with your certificate installed on the web browser.

## DIRAC User

Once you have your grid certificate and VO membership, you will be included as DIRAC user 

After getting a confirmation via Email, check if you can access https://dirac.cc.kek.jp:8443/DIRAC/ 

If you cannot access the web portal, you may not have your certificate imported into your web browser, or your certificate on the browser may not be the right one.

## More details 

Look at [Computing GettingStarted](https://xwiki.desy.de/xwiki/bin/view/BI/Belle%20II%20Internal/Computing%20WebHome/Computing%20GettingStarted) on XWiki.

