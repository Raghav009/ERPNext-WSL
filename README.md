# ERPNext-WSL
 ## If you have aready setup WSL then start from Installing Git in you wsl distro
## Install WSL in Windows
    wsl --install
  ### Restart PC
## Install Ubuntu WSL
    wsl --install -d Ubuntu
  
## Setup User in WSL ubuntu , Open Ubuntu in the Windows Terminal and run the below commands

## Install git
    sudo apt update
    sudo apt-get install git

## install python-dev
    sudo apt-get install python3-dev

## Install setuptools and pip (Python's Package Manager).
    sudo apt-get install python3-setuptools python3-pip

## Install virtualenv    
    sudo apt-get install virtualenv
    sudo apt install python3.10-venv

## Install MariaDB
    sudo apt-get install software-properties-common
    sudo apt install mariadb-server
    sudo mysql_secure_installation
    
      In order to log into MariaDB to secure it, we'll need the current
      password for the root user. If you've just installed MariaDB, and
      haven't set the root password yet, you should just press enter here.

      Enter current password for root (enter for none): # PRESS ENTER
      OK, successfully used password, moving on...
      
      
      Switch to unix_socket authentication [Y/n] Y
      Enabled successfully!
      Reloading privilege tables..
       ... Success!
 
      Change the root password? [Y/n] Y
      New password: 
      Re-enter new password: 
      Password updated successfully!
      Reloading privilege tables..
       ... Success!

      Remove anonymous users? [Y/n] Y
       ... Success!
 
       Disallow root login remotely? [Y/n] Y
       ... Success!

       Remove test database and access to it? [Y/n] Y
       - Dropping test database...
       ... Success!
       - Removing privileges on test database...
       ... Success!
 
       Reload privilege tables now? [Y/n] Y
       ... Success!
  ### Remember the Root Password of the DB (root)
## MySQL database development files

    sudo apt-get install libmysqlclient-dev

## Edit the mariadb configuration ( unicode character encoding )

    sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf

### Add this to the 50-server.cnf file

    [server]
    user = mysql
    pid-file = /run/mysqld/mysqld.pid
    socket = /run/mysqld/mysqld.sock
    basedir = /usr
    datadir = /var/lib/mysql
    tmpdir = /tmp
    lc-messages-dir = /usr/share/mysql
    bind-address = 127.0.0.1
    query_cache_size = 16M
    log_error = /var/log/mysql/error.log
    
    [mysqld]
    innodb-file-format=barracuda
    innodb-file-per-table=1
    innodb-large-prefix=1
    character-set-client-handshake = FALSE
    character-set-server = utf8mb4
    collation-server = utf8mb4_unicode_ci      
     
    [mysql]
    default-character-set = utf8mb4
## Update the Field in the Editor
    collation-server=utf8mb4_unicode_ci  
  Find collation-server in the 50-server.cnf <br />
  changes <code>collation-server=utf8mb4_general_ci</code> to  <code>collation-server=utf8mb4_unicode_ci</code>   
        
## Now press (Ctrl-S and Ctrl-X) to exit Editor and restart DB
    sudo service mysql restart

## Install Redis
    sudo apt-get install redis-server

## Install Node.js 16.X package
    sudo apt install curl 
    curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
    source ~/.profile
    nvm install 16

## Install Yarn
    sudo apt-get install npm
    
    sudo npm install -g yarn

## Install wkhtmltopdf
    sudo apt-get install xvfb libfontconfig wkhtmltopdf
    
## Install frappe-bench
    sudo -H pip3 install frappe-bench==5.10.1
    
    bench --version
    
## Initilise the frappe bench & install frappe latest version 
    bench init frappe-bench --frappe-branch version-14
    
    cd frappe-bench/
    
## Install ERPNext latest version and other Apps
    bench get-app payments
    
    bench get-app erpnext --branch version-14
    
## Create a site in frappe bench     
    bench new-site test.localhost
  ### Remember the Password for Administrator (admin)
  
## Set bench developer mode on the new site    
    bench --site test.localhost set-config developer_mode 1
    
    bench --site test.localhost clear-cache  
## Add Apps to Site test.localhost
    
    bench --site test.localhost install-app payments
    
    bench --site test.localhost install-app erpnext
    
    bench start
  ### Wait for 3 mins 
## Open the Site in the Brower 
    http://test.localhost:8000
  ### use the Details 
      Administrator:admin
    
