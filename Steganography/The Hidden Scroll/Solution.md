<b>The Flag for this challenge was divides into 4 parts.</b>
<br>
![Link to the image](/Steganography/The%20Hidden%20Scroll/src/hidden_scroll.png)
</br>

Note:- **Change the header file from png to jpg**

1st Part:- strings hidden_scroll.jpg

![alt text](/Steganography/The%20Hidden%20Scroll/src/image.png)

2nd Part:-
Using **Steghide** to extract hidden data/file in the jpg file.
<br>
Command:- steghide extract -sf hidden_scroll.jpg

![alt text](/Steganography/The%20Hidden%20Scroll/src/Part%202.png)


3rd Part:- Using <b>Exiftool</b> on the png file.
<br>
![Link to the image](/Steganography/The%20Hidden%20Scroll/src/Exiftool.png)

Encrypted Text:- **5fMKwQh5HDvofa5Ghd5uGEuGr**

This text is encrypted ***Base 58 Cipher***

Decrypted Text:- **part3: c0uld_f1nd_**

<br>
4th Part:- Using binwalk to extract hidden files
<br>
Command:- binwalk -e hidden_scroll.jpg

![alt text](/Steganography/The%20Hidden%20Scroll/src/Part%204.png)

Complete Flag:- **DJSISACA{D1dn't_th1nk_y0u_c0uld_f1nd_th3_fl4g_h3r3_t00}**