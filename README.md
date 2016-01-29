
#Steps to follow setup MyCaptionLabsUI(Frontend) project :- 

Step 1 :- Take the clone from git repository https://github.com/mediacatapult/MyCaptionLabsUI.

Step 2 :- Install bracket editor for developement and import project into bracket.

Step 3 :- Install node, grunt, npm, sass, ruby for packaging and run 'grunt' command on project root folder for packaging.

Step 4 :- Install nginx and update default configuration of ngnix by edit /etc/nginx/sites-enabled/default file with below content :

	server {
		listen 80;
		#listen 443 ssl;
		root /home/oodles/git/MyCaptionLabsUI/caption_lab_ui_build;  #Change it according to your project folder
		index /main.html;
		
		#Make site accessible from http://localhost/
		server_name localhost;
		#ssl_certificate /etc/nginx/ssl/nginx.crt;
        	#ssl_certificate_key /etc/nginx/ssl/nginx.key;

	location / {
		index /main.html;
		try_files $uri $uri/ /main.html;
	}
	location /static_content{
	  	alias  /home/mycaptionlab;
	}
	
	location /email_verification {
		try_files $uri $uri/ /views/user/email-verification.html;
	}
	location /calanderPrint {
		try_files $uri $uri/ /views/main/print-calender.html;
	}
	location /api {
		proxy_set_header X-Real-IP $remote_addr;
		proxy_set_header Host $host;
		proxy_pass http://localhost:8080/api;
			
	}
	}

Step 5 :- Start ngnix via 'sudo service nginx start'. This will deploy project on port 80 and you can check it on browser with http://localhost.


For UI Development, Brackets Editor (http://brackets.io/) is used with following Extensions installed: 1) Brackets Shell 2) Beautify 3) Brackets Icons 4) Document Toolbar 5) Ordered Ctrl+TAB Navigation 6) Brackets Git

File name convention: 1. All File name should be in lowercase and words are separated by "-". 2. Angular JS File convention 1. Services file name should be end with service eg. my-service.js 2. Controller file name should be end with controller eg. my-controller.js 3. same as other file 3. HTML, JS File should be place in their respective module


