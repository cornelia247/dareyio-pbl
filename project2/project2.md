# Project 2
- Darey masterclass project two lets say a continuation of project one where instead of working with LAMP we move into LEMP stack
- I SSH into the instance using my windows subsytem for linux 

- I also ran a system update as usual. 
## Now unto the Project
- I was tasked to create a **LEMP** stack infrastructure/environment installed my Nginx server using the command `sudo apt install nginx` I also checked the status of the server.
![](./screenshots/Screenshot%20(113).png)
2. We now have a webserver runing and we need a database to persit our data for that we need to install and set up MySql I used a password so i had to configure a strong password  for it
![](./screenshots/Screenshot%20(107).png)
![](./screenshots/Screenshot%20(108).png)
3. Unto the Next which is installing and configuring our php a simple ` sudo apt install php libapache2-mod-php php-mysql` helped in installing all the necessary tools needed for installing our PHP lang
![](./screenshots/Screenshot%20(109).png)
4. Creating a virtual host for our new project is where the fun is.
- we created a directory for our new project `sudo mkdir /var/www/projectLEMP`
- then we changed ownership to allow apache execute the files that would be in it by running ` sudo chown -R $USER:$USER /var/www/projectLEMP`
- We created, and updated the sites-available directory using nano `sudo nano /etc/nginx/sites-available/projectLEMP`
![](./screenshots/Screenshot%20(114).png)
- `sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/` was used to activate our config file and `sudo nginx -t` was used to test for syntax errors
- Next we disable the default nginx host that uses port 80 so we can access it with our new upcoming file,we did that with `sudo unlink /etc/nginx/sites-enabled/default`and did a nginx reload.
- next we created our hello world script and saved it to a html file using `sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html` and accessed it from the browser
5. Now just like our LAMP project we are creating an info.php script and try to access it from the browser, we did that with `sudo nano /var/www/projectLEMP/info.php` and made a php code to display our php info and VIOLA! it worked!
![](./screenshots/Screenshot%20(111).png)
6. Now for the fancy part, we are going to work with the MySql database we created earlier by creating a todo list, populating the database and querying it. 
- First we enter the mysql terminal with `sudo mysql`
- Create a database `CREATE DATABASE `new_database`;`
- Create a user with a strong password ` CREATE USER 'new_user'@'%' IDENTIFIED WITH mysql_native_password BY 'password';`
- Give user permissions to the database `GRANT ALL ON new_database.* TO 'new_user'@'%';`
![](./screenshots/Screenshot%20(116).png)
- Now lets test if the user has the given permissions with: `mysql -u example_user -p`, it prompt for the password and we are in!
- `SHOW DATABASES;` will give the present database in a interesting form;
![](./screenshots/Screenshot%20(117).png)
- lets create the tables:
![](./screenshots/Screenshot%20(118).png)
![](./screenshots/Screenshot%20(119).png)
- exit and lets create our todo_list.php using `nano /var/www/projectLEMP/todo_list.php` and edit the configuration to allow querying of the database
- After closing the file I tried accessing it from my browser but it was giving me a 403 error which got me panicing, I checked my errors.log file and found out my server was missing a module php7.4-fpm, I installed it, restarted my server and php and re-ran the codeand success!! 
![](./screenshots/Screenshot%20(121).png)
![](./screenshots/Screenshot%20(122).png)
![](./screenshots/Screenshot%20(120).png)
