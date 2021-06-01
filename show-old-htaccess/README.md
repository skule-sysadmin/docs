# Old .htaccess Files

If you have encountered an HTTP 500 error after the transition to Plesk, it might be because of outdated commands in your `.htaccess` file. The two commands you are likely to have are `php_flag` and `php_value`.

## How to fix

1. Log in to the Plesk web panel
2. Click on `FTP Access` and then on the account name (something along the lines of `sub_(numbers)`.)
3. Come up with a password following the advice [here](https://xkcd.com/936/).
4. Select `bin/bash` (or your preferred shell) for `Access to the server over SSH` then click OK. Note that not all shells are available.
5. Connect to the server using SSH. Use [this guide](https://support.plesk.com/hc/en-us/articles/115000172834-How-to-connect-to-a-Plesk-server-via-SSH-with-available-server-s-credentials) if you don't know how to. Use the username of the FTP account and the password you just created.
6. Type `cd` and press enter to navigate to your home directory.
7. Get the script by using `wget https://raw.githubusercontent.com/skule-sysadmin/docs/main/show-old-htaccess.sh`
8. Give yourself permission to run the script by using `chmod u+x show-old-htaccess.sh`
9. Run the script by doing `./show-old-htaccess.sh`. The script will output (something along the lines of) the following, then list where the outdated commands are used

```
------------------------------------------------------------------------------------------------------------------------
This script shows you where you have the old php_flag and php_value commands in your .htaccess files.
It will NOT delete these commands, nor will it change your php.ini file.
For safety, please do the changes manually and after a full backup.
------------------------------------------------------------------------------------------------------------------------


Occurances of the words "php_flag" or "php_value" under www
The format is:
path/to/file:line_number <line>
```

10. If there are more lines, follow [this](https://support.plesk.com/hc/en-us/articles/115001152233-How-to-customize-PHP-settings-in-Plesk) guide to update those settings to the values shown.
11. Finally, delete the listed lines from the listed lines using the `File Manager` in the Plesk web panel
