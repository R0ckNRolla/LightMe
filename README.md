<h1 align="center">
  LightMe
  <br>
</h1>

LightMe is a Simple HTTP Server serving Powershell Scripts/Payloads after Obfuscate them
and run obfuscation as a service in backgroud in order to keep obfuscate the payloads 
which giving almost new obfuscated payload with each HTTP request 

### Main Features
- Obfuscate all powershell files within the submitted directory
- HTTP Server to serve the obfuscated Powershell Files
- Background Obfuscator
- Almost new Payload in each request , (depanding on ```python obfuscate_interval```) 
- Powered by [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation)

### TODO
- Add more Invoke-Obfuscation Commands
- Improve the HTTP Server

### Install
```
git clone https://github.com/WazeHell/LightMe.git
cd LightMe/

# install powershell
sudo apt-get install powershell


# Run
python3 lightme.py /path/to/powershell_scripts/

```

### Running as services
```
#install supervisor
sudo apt-get install supervisor

sudo vim /etc/supervisor/conf.d/lightme.conf

# edit the config
[program:lightme_server]
directory=/lightme_path/
command=/usr/bin/python3 lightme.py /path/to/powershell_scripts/
numprocs=1
user=yourusername
autostart=true
autorestart=true
stdout_logfile=/lightme_path/lightme_std.log
stderr_logfile=/lightme_path/lightme_stderr.log
redirect_stderr=true
priority=999
stdout_logfile_maxbytes=5MB
stderr_logfile_maxbytes=5MB
environment=LANG=en_US.UTF-8,LC_ALL=en_US.UTF-8


# Run
sudo service supervisor restart
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl restart all
```