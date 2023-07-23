![](1.png)
If we follow the link, we will see the usual authorization form 
![](2.png)
Next, click on "Register" and create an account with a random name and password
We will see a code in which we will be interested in the selected line. It means that the user "admin" is set to "user_id" = 0. Further, if the "session_id" and "user_id" of the admin are the same, then the flag is displayed
![](3.png)
Go to Burp Suit and change "session_id"
![](4.png)
and get the flag
![](5.png)
