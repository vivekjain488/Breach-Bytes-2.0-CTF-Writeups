1) Download the image
2) Use **binwalk** to extract any hidden files in the image
```sh
binwalk -e chall.jpg --run-as=root
```

3) Found an **Untitled.jpg** file

![Pasted image 20241016233311](https://github.com/user-attachments/assets/8ec18e41-de2d-4190-9a3f-af2af90105d7)


Opening the image, we find some musical notes:

![Pasted image 20241016234309](https://github.com/user-attachments/assets/77943f3a-fefd-46de-95c3-a588edba655a)


4) Decryped this musical note with Acere cipher
Link: https://www.dcode.fr/acere-cipher

![Pasted image 20241017000123](https://github.com/user-attachments/assets/22bdd9b8-1cdd-48ae-857f-119f7e2458cd)


However, this isn't the flag, this is the password to decrypt the image.
Password: **ACEREISFUNTOPLAY**

Flag: **DJSISACA{MU52C4L_l0l}**
![Pasted image 20241017000229](https://github.com/user-attachments/assets/e3140798-044b-497a-ad33-4e9894976731)

