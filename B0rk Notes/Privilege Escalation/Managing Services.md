Managing Services

Starting a system service:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
systemctl start [servicename]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Ex. Apache2\ssh\etc.

Checking if a service is running:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ss -antlp | grep [servicename]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enabling a service at boot:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
systemctl enable [servicename]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Identifying services available to run:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
systemctl list-unit-files
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
