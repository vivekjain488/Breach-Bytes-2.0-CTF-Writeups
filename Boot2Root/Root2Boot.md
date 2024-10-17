1) Ran an nmap scan & found 2 interesting ports: **22 & 3000**
2) Visited Port 3000 & it shows a Login Page
3) Clicked on Forgot Password & tried to change the **admin** password but JavaScript blocks it
4) This is the source code of the JS that blocks the password change. The solution is simple, disable JavaScript in your Firefox browser
```
about:config
javascript.enabled
```

5) Now change the password. It's successful
6) After logging in, it takes us to a page where we can read local files (LFI)
7) Went 3 directories behind & read the `/etc/passwd` file. It contains the user *hacker*
8) Read the `id_rsa` of hacker user, copied in my system, changed the permissions & logged in as that user
9) Read `flag.txt` & got to know the flag is the root's original password
10) Read `convention.txt` in `/opt` & got to know the password policy. Basically we have to create wordlist with all the 6 digit numbers in between the username & reversed username.
11) Checked for SUID binary, got `cp` binary which can be exploited
12) Copied the `/etc/passwd` in my local machine & inserted a new user which has root privileges
13) Then I downloaded the modified `passwd` file to the target machine and used `cp` to change the original `/etc/passwd` with the modified one.
14) Read the `/etc/shadow` file to get the hashed password of root.
```sh
# Root Password
$6$LHo9xrJts.a/1lTl$yIwh3VpO8FD5tohJZBeqNMQ4pWK37oH1OkqFCxTLgnw/z3b3bySWNd1Qa/E4jIvibj45S.DB4XgYcIVtQI8bQ1
```

15) Generated a wordlist according to the password convention
```python
with open("root_password_wordlist.txt", "w") as file:
    # Loop through all 6-digit numbers from 000000 to 999999
    for i in range(1000000):
        # Format the number to be 6 digits with leading zeros
        password = f"root{i:06}toor"
        # Write the password to the file
        file.write(password + "\n")

print("Wordlist created: root_password_wordlist.txt")
```

16) Run the Python script to get the wordlist
17) Use **John the Ripper** with the wordlist to get the original password
```sh
john hash --wordlist=root_password_wordlist.txt
```

Since I've already done it, I'll just show you the password