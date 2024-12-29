# Stones
![image](https://github.com/user-attachments/assets/9bbf080a-c049-49bd-862d-f2fbf4ca4899)

# Attachment :
https://student2024.wargames.my/files/2e9c12f155cae55326d86dcc0c4e82bf/stones.whatdis?token=eyJ1c2VyX2lkIjoyMDEsInRlYW1faWQiOjkwLCJmaWxlX2lkIjoyOX0.Z3Fthw.sqR2lCLSZg-jOuPEdEJr_bYhAX0

# Solution :
In this challenge, we are only provided with one file with a weird extension.
![image](https://github.com/user-attachments/assets/e7f84dd0-ed8b-4b00-8b2e-f13a9d798663)
<br>
<br>
As usual, always check file type and its strings content to know what the file is made of.
In this case, the file is a Windows executable and code with python.
`file stones.whatdis`
![image](https://github.com/user-attachments/assets/83502020-b4fe-41b0-a684-e0ede0477e6e)
`strings stones.whatdis`
![image](https://github.com/user-attachments/assets/e1a38061-ea2f-4190-992b-834193f10d32)
<br>
<br>
We know is a Windows executable and also python file at the same time, but what is the weird extention for?
Welp, there a quite a lot of ctf with this kind of challenge, when you see a python or upx at the last line of the string output, the challenge file is packed by a packer.
Here is a write-up link that explains this kind of challenge [PICO CTF packer](https://dev.to/yowise/picoctf-2024-packer-5h0l) 
Right now we confirm the file is definitely packed.
![image](https://github.com/user-attachments/assets/e7038ff8-131e-4072-94b5-10e7bfc0b987)
<br>
<br>
Now we extracted those files out with [Pyinstractor](https://pyinstxtractor-web.netlify.app/)
![image](https://github.com/user-attachments/assets/e780b37e-cd74-4d41-8b0e-74e3ce463988)
![image](https://github.com/user-attachments/assets/07203a54-6f98-4e0f-8b57-12c0b4ba8ed6)
<br>
<br>
There are a lot of files but we only need the CHAL-stones.pyc challenge file
Now we need to decompile the pyc file using [PyLingual](https://pylingual.io/)
![image](https://github.com/user-attachments/assets/3c51417c-f2b5-435a-b681-bde9efb9cc18)
<br>
<br>
Looking into the file, we already have first part of the flag
![image](https://github.com/user-attachments/assets/de1280e3-29cb-4ce6-8cae-e8f9f7d7f262)
<br>
<br>
Right now we need to get the full flag from the server, in the description it mention there is a slash flag AKA /flag on the server 
![image](https://github.com/user-attachments/assets/325d2454-f258-4d34-8b77-9504d76b06db)
![image](https://github.com/user-attachments/assets/2ba5fc57-2773-4ab0-bdaa-7cb03672519a)
<br>
<br>
At the /flag server, we only have a youtube link to MARVEL Avengers : Endgame movie
![image](https://github.com/user-attachments/assets/2d299e71-758f-4823-acac-8ea64525fe2c)
<br>
<br>
So with all the information, here is the logic.
The whole local date check with the current date is just a distraction, it won't give you the flag.
So we coming to the get request part where we will be send a parameter payload to the server
`params = {'first_flag': first_flag, 'date': user_date}`
The user_date we will change it to the date of the premier of the youtube video then send it to the server together with the first part of flag.
![image](https://github.com/user-attachments/assets/d1f4a46a-5d03-4255-96ab-5e3a3ae94134)
<br>
<br>
Here we go, we gotthe flag.
![image](https://github.com/user-attachments/assets/1cc10696-eff7-4a4c-9a9d-2bd89e044a70)


