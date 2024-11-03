# Task
The developers here at the Haunted Brewery have been experimenting with hot keys in attempts to keep out 👻, Spirits, Poltergeists and Banshees from accessing the our development `/login` site. We figure lack of fingers should prevent them from bypassing the default DENY ALL, "HUMANS ONLY" captcha and get a client-side authorization token.

> Off Topic: You will see a references to one of my favorite movies in the challenge. If you know the movie, it should help identify components of the challenge: [Fifth Element](https://www.imdb.com/title/tt0119116)

THIS FLAG will be CTF{flag_here_format}

Connect to the challenge: [https://hackersnhops-fcaptcha.chals.io](https://hackersnhops-fcaptcha.chals.io/)

[https://hackersnhops-fcaptcha.chals.io](https://hackersnhops-fcaptcha.chals.io/)

# Write-up
at the beginning, you can inspect the page element and you can see that a js-script is used here

![alt text](<Pasted image 20241103112152.png>)

```js

        const checkboxLabel = document.querySelector('.captcha-text');
        const checkbox = document.getElementById('captchaCheck');
        const tokenInput = document.getElementById('tokenInput');
        const cookieImage = document.getElementById('cookie-image');

        let ctrlKeyHeld = false;
        let checkboxChecked = false;

        checkbox.addEventListener('mouseover', function() {
            if (!checkbox.checked) {
                checkboxLabel.textContent = "I am not human";
            }
        });

        checkbox.addEventListener('mouseout', function() {
            if (!checkbox.checked) {
                checkboxLabel.textContent = "I am human";
            }
        });

        checkbox.addEventListener('change', function() {
            if (checkbox.checked && checkboxLabel.textContent === "I am not human") {
                alert("Since you indicated you are not human, you may not proceed.");
                checkbox.checked = false;
            }
        });

	document.addEventListener('keydown', function(event) {
	    if (event.key === 'Control' || event.key === 'Meta') {
		ctrlKeyHeld = true;
	    }
	    if (ctrlKeyHeld && event.key === 'f') {
		event.preventDefault();
		if (checkbox.checked) {
		    setCaptchaToken('valid_token');
		    window.location.href = '/login'; // Redirect to login page
		}
	    }
	});
        
        document.addEventListener('keyup', function(event) {
            if (event.key === 'Control' || event.key === 'Meta') {
                ctrlKeyHeld = false;
                checkSubmitConditions();
            }
        });

        checkbox.addEventListener('change', function() {
            checkboxChecked = checkbox.checked;
            checkSubmitConditions();
        });

        function checkSubmitConditions() {
            if (ctrlKeyHeld && checkboxChecked) {
                setCaptchaToken('valid_token');
            }
        }

        function setCaptchaToken(token) {
            tokenInput.value = token;
            localStorage.setItem('captchaToken', token);
            document.getElementById('captchaForm').submit();
            showCookieImage();
        }

        function showCookieImage() {
            const storedToken = localStorage.getItem('captchaToken');
            if (storedToken) {
                cookieImage.style.display = 'block';
            }
        }
    
```

you can see that you can successfully click on the captcha and go to the `/login` page only with `ctrl` pressed
after that, you can change the authorization key through the `burp suite`

![alt text](<Pasted image 20241103112038.png>)

![alt text](<Pasted image 20241103111957.png>)

you can see a hint that you need to use `base64` ![file](1.dat)

![alt text](<Pasted image 20241103111939.png>)

after decoding the strings, you can use the `010editor` to view the file signature
this is a `png` image, but the first byte is broken in it
by correcting them, we can get a flag

![alt text](<Pasted image 20241103112233.png>)

![alt text](<Pasted image 20241103112202.png>)

Flag: `CTF{n3gAt1v3_I_am_4_m34t_p0p5icl3}`