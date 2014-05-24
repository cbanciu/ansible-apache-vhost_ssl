###<strong>Ansible playbook to add an Apache ssl virtual host. On Debian the config is added to /etc/apache2/sites-available/ while on RHEL is added to /etc/httpd/conf.d/. See apache_dir variable for that. Does reload apache. </strong> 

***
<strong>Usage:</strong> <br />
ansible-playbook -i inventory vhost_ssl.yml
***

***
<strong>Checks:</strong> <br />
1. Cert md5sum matches key md5sum <br />
2. Cert CN matches Apache ServerName. I suppose this might break SAN certificates. <br />
Both conditions must be valid in order for the SSL certificate to be installed
*** 

<strong>Explanation for each variable:</strong>

site_url ==> Self explanatory. Make sure it's identical with SSL Common Name value. <br /> 
apache_ssl_port ==> Default 443. <br />
log_format ==> Apache log format. <br />
apache_docroot ==> Virtual Host DocumentRoot. <br />
ssl_ip ==> Virtual Host Listening IP. <br />
cert_file ==> Local certification file which will be copied to the remote host. Default name: cert <br />
key_file ==> Local key file to be copied to the remote host. Default name: key <br />
ca_file ==> Local CA bundle to be copied to the remote host. Default name: CA <br /?

OS family variables:

apache_logs ==> Full path to apache log folder. <br />
apache_dir ==> Full path to apache configuration folder. <br />
apache_group ==> Apache group

***
<strong>TO DO:</strong> <br />
* Better documentation
* Verify CA
* Tweak SSL ciphers
 
