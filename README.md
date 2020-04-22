# safe_password_checker
See how many times your is password hacked in a safe way. Python 3. requests package needed.


We request frequently updated 'hacked passwords' data from  https://haveibeenpwned.com/Passwords
The website itself uses SHA1 hash to store passwords.*(see below)


This code takes your password(passwords) from console and turns them into SHA1 hash.
Then it takes the first 5 character of your SHA1 hash and request all the codes matches with this first 5 characters of your code from the website.(This is safe because you don't share your code with the website so it is not stored in their logs). Then it finds your code among the list of codes requested and chekcs if your password is hacked before.And how many times. 
The more times the password is hacked, more dangerous it is to use it. Anyway you should consider changing your password even if it's hacked onces.




Why Hashes?(from author of the site)*
Sometimes passwords are personally identifiable. Either they contain personal info (such as kids' names and birthdays) or they can even be email addresses. One of the most common password hints in the Adobe data breach (remember, they leaked hints in clear text), was "email" so you see the challenge here.

Further to that, if I did provide all the passwords in clear text fashion then it opens up the risk of them being used as a source to potentially brute force accounts. Yes, some people will be able to sniff out the sources of a large number of them in plain text if they really want to, but as with my views on protecting data breaches themselves, I don't want to be the channel by which this data is spread further in a way that can do harm. I'm hashing them out of "an abundance of caution" and besides, for the use cases I'm going to talk about shortly, they don't need to be in plain text format anyway.

Each of the 306 million passwords is being provided as a SHA1 hash. What this means is that anyone using this data can take a plain text password from their end (for example during registration, password change or at login), hash it with SHA1 and see if it's previously been leaked. It doesn't matter that SHA1 is a fast algorithm unsuitable for storing your customers' passwords with because that's not what we're doing here, it's simply about ensuring the source passwords are not immediately visible.

Also, just a quick note on the hashes: I processed all the passwords in a SQL Server DB then dumped out the hashes using the HASHBYTES function which represents them in uppercase. If you're comparing these to hashes on your end, make sure you either generate your hashes in uppercase or do a case insensitive comparison.



for more info about where are the passwords from, how they store them etc. 
read https://www.troyhunt.com/introducing-306-million-freely-downloadable-pwned-passwords/



