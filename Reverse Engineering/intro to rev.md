1. First I opened the file given in ghidra since it was an ELF executable
2. Then I looked over the decompiled main function and saw that it is basically it is basically comapring the inputted string by the user to the value in the variable constants 
   ![image](https://github.com/user-attachments/assets/a589087c-8eb2-494d-b024-811415ebc22d)
3. Then I found the location of the variable constants and  wrote down its contents in hex and converted it into ascii : }GnIReENigne_E5rEVer_07_0r7NI{ACASISJD
   ![image](https://github.com/user-attachments/assets/4fc076b4-7099-42d1-bd46-e57246ab1129)
4. And in the super_secure_encode function used in main we could  see that the input is reversed to compare, so we reverse the string and get our flag **DJSISACA{IN7r0_70_reVEr5E_engiNEeRInG}**
![image](https://github.com/user-attachments/assets/b413eb42-b1ab-4c0f-876d-b008700cbfce)
