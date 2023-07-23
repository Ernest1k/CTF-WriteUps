![](1.png)
If we follow the link, we will see the usual authorization form 
(Если мы перейдем по ссылке то увидим обычную форму авторизации)
![](2.png)
Next, click on "Register" and create an account with a random name and password
We will see a code in which we will be interested in the selected line. It means that the user "admin" is set to "user_id" = 0. Further, if the "session_id" and "user_id" of the admin are the same, then the flag is displayed
Далее нажмем на "Register" и создадим аккаунт со случайным именем и паролем
Перед нами появится код, в котором нас будет интересовать выделенная строка. Она означает, что пользователю "admin" устанавливается "user_id" = 0. Далее если "session_id" и "user_id" админа совпадают, то выводится флаг
![](3.png)
Go to Burp Suit and change "session_id"
Перейдем в Burp Suit и изменим "session_id"
![](4.png)
and get the flag
и получим флаг
![](5.png)
