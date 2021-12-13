# GVE_DevNet_Meraki_Device_Status_Email_Reporter
prototype script that queries the status of all offline Meraki devices and sends a detailed report through email (smtp)


## Contacts
* Jorge Banegas

## Solution Components
* Meraki
* Mongo Database
* SMTP

## Installation/Configuration

(optional) This first step is optional if user wants to leverage a virtual environment to install python packages

```shell
pip install virtualenv
virtualenv env
source env/bin/activate
```

Install python dependencies 

```shell
pip install -r requirements.txt
```

Include configuration details for SMTP server, Meraki API key and Mongo database

![/IMAGES/config.png](/IMAGES/config.png)


## Usage

To launch the collector script (this script collects device downtime from the previous day):


    (env) $ python collector.py 
   

To launch the emailer script (this script sends the email report):


    (env) $ python main.py
    
If the script is unable to send out an email, try removing the SSL inside the main.py file (line 247) 

from 
    ```
        smtp_server = smtplib.SMTP_SSL(config.smtp_domain, 465)
    ```
to 
    ```
        smtp_server = smtplib.SMTP(config.smtp_domain, 465)
    ```
    
    
If everything works out, you should see the terminal send out a confirmation whenever an email report is sent over.

    ```python
        Email sent successfully!
    ```
    
 
# Screenshots
Example of email that is sent over 

![/IMAGES/0image.png](/IMAGES/example.png)

### LICENSE

Provided under Cisco Sample Code License, for details see [LICENSE](LICENSE.md)

### CODE_OF_CONDUCT

Our code of conduct is available [here](CODE_OF_CONDUCT.md)

### CONTRIBUTING

See our contributing guidelines [here](CONTRIBUTING.md)

#### DISCLAIMER:
<b>Please note:</b> This script is meant for demo purposes only. All tools/ scripts in this repo are released for use "AS IS" without any warranties of any kind, including, but not limited to their installation, use, or performance. Any use of these scripts and tools is at your own risk. There is no guarantee that they have been through thorough testing in a comparable environment and we are not responsible for any damage or data loss incurred with their use.
You are responsible for reviewing and testing any scripts you run thoroughly before use in any non-testing environment.
