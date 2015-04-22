# curllogin
Remote login with CURL

The curl extension of php can be used to open remote webpages by both GET and POST methods. There are many situations when you need a php script to login into a website and open a certain page. For example when you are writing a bot or web scraper. 

To login we need 2 important piece of information :

1. The URL to which login data should be submitted. This can be for example : www.somesite.com/login.php

2. The format of the login data , like username and password. It is important to know how the post data is being send to the remote website. Is it username or user or uname or what ?

To find this out simply use the inspector tool in google chrome/firefox. Activate the inspector's network tab first and then login into the website. The inspector will show which Url was used and what data was posted.
Now all you need to do is post the same data to the same url from your script. Simple!!

Lets say your Url is www.somesite.com/login.php
And the login post data is 

username : some_username&password=some_password

After the curl_exec the login page is opened with login details or simply the login has been DONE.

Now any other login protected url can be opened as :

curl_setopt($ch, CURLOPT_URL, $url);
curl_exec($ch);

The option CURLOPT_COOKIEFILE is used to specify a file which stores the cookie data that is received during the process of opening and logging into webpages. Make sure the directory is writeable by php so that it can create these files. If the cookie directory is not writable , the cookies wont be created and login will not persist. 

The login page of the particular site where the username and password are asked for, will give various information regarding the name of fields to be send as username, password, the type of query that is POST, the form submission url to which the values are to be submitted etc. Use dom inspector in google chrome or firebug in firefox to find out the field names.

Those information should be used in the above code to specify the login url , username and password field names and values etc. The same exact steps should work with ssl or https urls provided the openssl module is enabled.
