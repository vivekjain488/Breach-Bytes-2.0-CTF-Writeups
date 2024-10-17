1) Ran an nmap scan & found 2 interesting ports: **22 & 3000**

![1](https://github.com/user-attachments/assets/15e3d120-6879-415a-a01a-4ef3640ffcac)

2) Visited Port 3000 & it shows a Login Page

![2](https://github.com/user-attachments/assets/3b7755e7-28da-4759-8d55-246f44075a0a)

3) Clicked on Forgot Password & tried to change the **admin** password but JavaScript blocks it

![3](https://github.com/user-attachments/assets/0b596a6e-b4de-4a8e-a0f0-8d7a167c1c01)

4) This is the source code of the JS that blocks the password change. The solution is simple, disable JavaScript in your Firefox browser
![4](https://github.com/user-attachments/assets/ba9fb10c-f460-43d6-9900-1c099684cff1)

Type in this in your Firefox browser. Then change the setting to **False**
```
about:config
javascript.enabled
```
![5](https://github.com/user-attachments/assets/4fbb467a-5612-49de-9fd9-9e42e6e03786)

5) Now change the password. It's successful!

![6](https://github.com/user-attachments/assets/8eb3c4f8-c878-4bc5-897a-9125356c94bd)

6) After logging in, it takes us to a page where we can read local files (LFI)

![7](https://github.com/user-attachments/assets/9eb27e70-a927-4172-aa9e-251babdcf08f)

7) Went 3 directories behind & read the `/etc/passwd` file. It contains the user *hacker*

![8](https://github.com/user-attachments/assets/679c0a5d-9b57-4097-806a-d8542708af2b)
![9](https://github.com/user-attachments/assets/e839a8ca-3676-4a58-b754-fea1979d481b)

8) Read the `id_rsa` of hacker user, copied in my system, changed the permissions & logged in as that user

![10](https://github.com/user-attachments/assets/ece8bdf2-bdf7-4af5-a67e-958e66151a26)
![11](https://github.com/user-attachments/assets/5218351c-657e-42d2-998f-f3f4b1397868)

9) Read `flag.txt` & got to know the flag is the root's original password
![12](https://github.com/user-attachments/assets/53e26145-f9da-4c7d-bf06-e1f53c072a92)

10) Read `convention.txt` in `/opt` & got to know the password policy. Basically we have to create wordlist with all the 6 digit numbers in between the username & reversed username.
![13](https://github.com/user-attachments/assets/d6d191ba-680a-465c-a1a2-84ca90c52bb6)

11) Checked for SUID binary, got `cp` binary which can be exploited

![14](https://github.com/user-attachments/assets/1b2dd0fc-6aec-4ed8-b207-84a3ed086092)

12) Copied the `/etc/passwd` in my local machine & inserted a new user which has root privileges

![15](https://github.com/user-attachments/assets/5bfd05bd-eb00-469f-b1fc-7bedfc754bdc)
![16](https://github.com/user-attachments/assets/6c29fbbe-427b-4af8-a0a0-dd5e56158f25)
13) Then I downloaded the modified `passwd` file to the target machine and used `cp` to change the original `/etc/passwd` with the modified one.

![17](https://github.com/user-attachments/assets/0643238a-38a3-4cca-a3b3-9c5e5f0c7b55)

14) Read the `/etc/shadow` file to get the hashed password of root.
```sh
# Root Password
$6$LHo9xrJts.a/1lTl$yIwh3VpO8FD5tohJZBeqNMQ4pWK37oH1OkqFCxTLgnw/z3b3bySWNd1Qa/E4jIvibj45S.DB4XgYcIVtQI8bQ1
```
![18](https://github.com/user-attachments/assets/f61f8eb3-fb2a-4784-92c6-9ba1a9df5866)

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
![19](https://github.com/user-attachments/assets/f257bc04-0615-47eb-84f2-9dfdc360483a)

17) Use **John the Ripper** with the wordlist to get the original password
```sh
john hash --wordlist=root_password_wordlist.txt
```

Since I've already done it, I'll just show you the password.
![20](https://github.com/user-attachments/assets/5b8dad87-dd01-4006-8662-cc26a47e78bd)

Flag: **DJSISACA{root600065toor}**
