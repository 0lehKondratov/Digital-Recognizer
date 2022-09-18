https://towardsdatascience.com/run-jupyter-notebook-as-a-background-service-on-ubuntu-c5d6298ed1e


mkdir -p /home/cruser/.local/share/virtualenvs/notebook/bin/jupyter-notebook 

sudo touch /etc/systemd/system/jupyter-notebook.service
sudo chmod 664  /etc/systemd/system/jupyter-notebook.service


jupyter-notebook.service

[Unit]
Description=Jupyter-Notebook Daemon

[Service]
Type=simple
ExecStart=/bin/bash -c "/usr/local/bin/jupyter-notebook --no-browser --notebook-dir=/home/cruser/works/Digital-Recognizer"
WorkingDirectory=/home/cruser/works/Digital-Recognizer
User=cruser
Group=cruser
PIDFile=/run/jupyter-notebook.pid
Restart=on-failure
RestartSec=60s

[Install]
WantedBy=multi-user.target