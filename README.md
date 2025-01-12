# SFTP files downloader Add-On for Splunk

> The **SFTP files downloader Add-On for Splunk** uses paramiko as a client to connect to an SFTP server and download files to your Splunk instance.

> NOTE: You will have to configure input stanza(s) to ingest your log files
> that were downloaded with this TA. We recommend using the batch input method
> unless you have other log rotation methods.

## Sample Configurations

### username password authentication

> This can be configured in the inputs configuration page or inputs.conf
> It is recommended to use the GUI to configure the inputs. See screenshot below

<img src="static/inputs.png"/>

```
[sftp_files_downloader://sample_source]
destination_file_path = /opt/splunk/etc/apps/TA-sftp-files-downloader/downloaded_files
interval = 3600
key_file_type = RSA
password = ******
port = 22
server_file_path = /upload
ssh_server = 0.0.0.0
username = sftp_user1
disabled = 0
burn_after_download = False
```

### private key and known_hosts authentication

> The known_hosts file and private key file will need to be manually added onto your Splunk server

```
[sftp_files_downloader://sample_source2]
burn_after_download = False
# The destination file path can be anywhere on your server
destination_file_path = /opt/splunk/etc/apps/TA-sftp-files-downloader/downloaded_files
interval = 3600
key_file_path = /opt/splunk/.ssh/private_key
key_file_type = RSA
port = 22
server_file_path = /upload
ssh_server = 0.0.0.0
ssh_server_known_hosts_path = /opt/splunk/.ssh/known_hosts
username = sftp_user1

```

### Sample known_hosts

```
[0.0.0.0]:22 ssh-rsa ...........
```

### Installation Instructions

This Add-on can be installed in **Splunk Enterprise** only.

## Credits & Acknowledgements

- Guo Huang
- Man Pham

## Support

Find us in splunk-usergroups.slack.com
