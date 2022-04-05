# Project 1
- Darey masterclass project one was created for us to get more familar working in the terminal for that we had to create an ubuntu virtual environment or an Elastic Cloud Compute instance using AWS
- I SSH into the instance using my windows subsytem for linux 

![](./screenshots/Screenshot%20(105).png)

- I also ran a system update as shown in the screenshot above. 
## Now unto the Project
- I was tasked to create a **LAMP** stack infrastructure/environment ( Linux Apache MySql PHP)
1. first I installed my Apache server using the command `sudo apt install apache2`, next I updated my security group inbound rule to allow access to port 80 by the internet, I also checked the status of the server and was glad to see green
![](./screenshots/Screenshot%20(100).png)
![](./screenshots/Screenshot%20(106).png)
![](./screenshots/Screenshot%20(101).png)
2. We now have a webserver runing and we need a database to persit our data for that we need to install and set up MySql I used a password so i had to configure a strong password  for it
![](./screenshots/Screenshot%20(107).png)
![](./screenshots/Screenshot%20(108).png)
3. Unto the Next which is installing and configuring our php a simple ` sudo apt install php libapache2-mod-php php-mysql` helped in installing all the necessary tools needed for installing our PHP lang
![](./screenshots/Screenshot%20(109).png)
4. Creating a virtual host for our new project is where the fun is.
- we created a directory for our new project `sudo mkdir /var/www/projectlamp`
- then we changed ownership to allow apache execute the files that would be in it by running ` sudo chown -R $USER:$USER /var/www/projectlamp`
- We created and edited our project config file with vim (why is Vim so complicated??)
![](./screenshots/Screenshot%20(110).png)
- `sudo a2ensite projectlamp` command enabled our virtual hosts, `sudo a2dissite 000-default` disabled the default website that came with apache, we did a system reload for apache, created an helloworld HTML file and viola! I had a working project that was accessable on the local and public IP:80, check out my errors all because I forgot to add Sudo to my code lol
![](./screenshots/Screenshot%20(102).png)
5. Now to bring everything together, while we I a working HTML file, that was not the goal of the project I needed a PHP file running in the server, but Apache default index file was HTML so we had to tweak the dir.config file to allow PHP files take precedence, after that a simple PHP code was created which purpose was to give a little bit info about PHP, we pushed that into our environment and ran our IP address on the internetand like i said Voila!! all was good with the universe
![](./screenshots/Screenshot%20(111).png)
- After that i cleared my environment to preserve the integrity of my work because of some sensitive data `sudo rm /var/www/projectlamp/index.php`

