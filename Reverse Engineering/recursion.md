1. First we open up the file in ghidra since it is again a ELF executable
2. Then we can open up the decompiled main function and see that the main logic behind checking input is working in validate_chars function
  ![image](https://github.com/user-attachments/assets/0f44df94-7346-44c9-9346-4d01d8218c71)
3. By understanding how the validate characters work we find out that we need to  reverse the contents of SECOND_HALF variable and take the content of FIRST_HALF as is and we would get the flag
   ![image](https://github.com/user-attachments/assets/e2f0c75d-67ab-45ad-8ad3-4411d66ffc6a)
4. The content of FIRST_HALF was: DJSISACA{3L!X!R 
  ![image](https://github.com/user-attachments/assets/68fc0082-9460-4581-9c42-0496588fbc24)
  ![image](https://github.com/user-attachments/assets/eb28c01b-1575-473e-b18f-cb9be436a9f1)
5.  The contents of the SECOND_HALF were }R!X!L3KR4D>---
   ![image](https://github.com/user-attachments/assets/e60e6247-d5ca-4f51-b6af-13a590d9517e)
   ![image](https://github.com/user-attachments/assets/10879920-b892-4b4e-a4ea-8cf108c41072)
7.  So the flag was : **DJSISACA{3L!X!R--->D4RK3L!X!R}**
