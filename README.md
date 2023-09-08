# test-cases-authentication-bypass


# OTP bypass :

  Generate an otp from the application and then enter an wrong otp then intercept the request using burp then do intercept the response for the request and then manipulate the response and bypass the otp. 

# Deletion of account without pass:

  update some information in the profile section and then capture the request in the burp then send it to repeater then change the put method to delete and send the request.
    this is only an vulnerability if the deletion of account needs any authentication.

# Username Enumeration:
  enter an random username and an constant password in the login page then intercept the request in burp then add n number of usernames as the payload and check for the 
    difference in the response then try to enumurate the passord then try to login using that username and password.

# Directory changing:
  login to the site using original id and then note the url of the webpage and then logout then try to login using another account and during the
    2FA change the directory to the profile that you noticed and check wether you are logged in.

# Token smuggling:
  create an change password request from your account and then intercept the request then enter the password and send the request to the repeater
    then erase the token and change the username to the victims username then send the request. finaly try to login with the password you provided
    for the victims account.for Reference (portswigger: password reset broken logic)

# bypassing the email verification while demo use time:

  in this case, the target should allow an user to use their applicaion for an limited period of time without verifying their email, in this case
    after the time expires, try replacing the url or the request with the old token and see wether you can use the application for another periond
    of time.

# BYpassing otp using character:

   in this case instead of entering the number as otp, enter an characters as otp and intercept the response of the request and observe the response of the application.
   if the response was 200 and there wasn't any message, enter 1 or true and check wether you can bypass the otp verification.

# Captcha bypass: 

   enter the wrong captcha and intercept the response of the request and modify the response to the success state and forward the request and check wether the captcha can 
   be bypassed.

# login into another account using response manipulation:
  give the right otp or the password then intercept the response for the request and then change the id value or the user token then check wether you get logged in into
        the other persons account.



# Username Enumeration via different response timing:

  capture the login request using burp and the bruteforce the username with an long password and check the response timing and try to bruteforce the accounts password

# Username Enumeratoin via logout bypass :

  in this case , the application should block the user for certain time if the user logs in with the same username and passwor for certain
        times and then the time should be reset if the user logs in with the right username and password. in this case, we should find the number 
        of incorrect password attempts possible and then we have to craft out payload according to the number of allowed attempts and bruteforce 
        the username and password.   For reference - portswigger(broken bruteforce protection, ip block)

# username enumeration via account lock:

  in this case the application doesnot restrict an invalid username to bruteforce the password while , too many request from an valid 
        username will be restricted. in this case, we have to enumerate the application by giving valid username list and then we have to select 
        the clusterbomb attack and then we have to select certain amount of null payloads that the applicaion restricts after. then bruteforce 
        the username and check the variation between status code or the content length and try to enumerate the username and do vice versa for 
        the password.

# OTP leak in the response:
  in this case, the response for the otp request itself contains the otp for the verification and so it makes the attacker to easily bypass it. to reproduce this, 
        send an request to the server requesting for otp then do intercept response for the request and check wether you can see any leakage of otp in the response.

# 2fa bypass using functionality bypass:
  use the application using your credentials and then record all the requests using burp then select the request which contains the username and otp provided for your 
        account then change the username to any other username and then bruteforce the otp then find any request with the response code 302 and then open the response in the 
        browser and check wether you are logged in as that user.(before you do this make sure you trigger an otp to the victims account by changin the username or email parameter
        in the burp and then brute force the otp then only this attack would work)

# Auth bypass using stay logged in cookie : 
   in this case , the application should have an stay logged in option and then we should be able to see the cookie of the stay logged in option. then we should try 
        to find the value of the cookie by decoding it and try the format of the cookie. then we have to bruteforce the cookie value and then try to log in to the another 
        account. while bruteforcing the cookie , we should remove the session cookie and the parameter and then the attack should be conducted.for reference:  (Lab: Brute-forcing a stay-logged-in cookie)

# Bruteforcing password in using current password functionality:
   in this case, the application logsout the attacker after a certain attempts of incorrect current password with the matching new password in the two confirmations including the confirm password field
        so , there is an application logic flaw in which the attacker is able to do many attempts when an wrong current password is given and the new password fields are mismatched. using this , the attacker can
        bruteforce the current password of the victim.

# sending multiple passwords with one username:

  in this case , we should send the username that we want to takeover with the multiple possible passwords and check wether we are getting logged in as the victim.


# middleware:
  in this case , we include the X-Forwaded-For and the include our server or email then check wether the mail reset password mail reaches the server and change the 
         password of the victims account.
