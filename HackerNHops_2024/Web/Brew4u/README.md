# Task
The Haunted Brewery Brew4u Contest is open to patrons who can design the best custom brew! Participants submit descriptions of their dream beer to the BrewMaster for a chance to have it featured in the taproom.

However, this year, something feels off. Rumors suggest the brewery's submission system is hiding a secret. Some say the legendary BrewMaster's secret-ingredient recipe is buried within the system, accessible only to those with a keen eye for detail.

Your mission: Submit a description for your custom brew, but be on the lookout—hidden within the system’s responses could be the clues you need to uncover the BrewMaster's secret recipe. The right approach might reveal more than just a drinkable masterpiece.

Connect to the challenge: [https://hackersnhops-stop-changing-the-flag.chals.io/](https://hackersnhops-stop-changing-the-flag.chals.io/)

[https://hackersnhops-stop-changing-the-flag.chals.io/](https://hackersnhops-stop-changing-the-flag.chals.io/)

# Write-up
when we sent data, we see that site have `/ssti` its men `SSTI injection`
for example ${{7*7}} -> 49

![alt text](<Pasted image 20241103112705.png>)

![alt text](<Pasted image 20241103112721.png>)

we can use the following command to see which command number to open a file in `Jinja2`

![alt text](<Pasted image 20241103115238.png>)

and now you can read the flag

![alt text](<Pasted image 20241103115434.png>)

Flag: `HnH{j1njA2_t3mpl4t3_1nj3cT}`
