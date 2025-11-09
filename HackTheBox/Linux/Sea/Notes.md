feroxbuster -u [https://10.10.10.250/manager/status/](https://10.10.10.250/manager/status/) --insecure
 
if you see 403 on a page that is supossed to be open then always try to bypass it
 
if you see a cron file if you can't edit it then alwayas try to read it an understand what it is doing
 
we also used ln command to link a folder to another locatiion when the cronfile named run.yml was looking for files the command was
 
ln -s /home/luis/.ssh /opt/backup/folder/uploads