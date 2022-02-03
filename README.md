## Email Encryption using Blowfish Algorithm
### Introduction


### Project
The Blowfish algorithm takes 64-bit plaintext as input and then gives an output of 64-
bit cipher text. The key length varies from 32 bits to 448 bits. The algorithm consists
of two main actions. One is the key expansion and the other is the data encryption.
During key expansion, a key of maximum size of 448 bits is converted into several
subkeys to a total of 4168 bytes. The original subkey p-box and s-box are fixed. After
key expansion, data encryption takes place in a 16-round Feistel network. A key
dependent permutation and a key and data dependent substitution takes place in each
round. The subkeys are computed ahead of any data encryption or decryption.

ENCRYPTION:
1. Divide X into two blocks XL and XR of equal sizes. Thus, both XL and XRwill
consist of 32 bit each
2. For I = 1 to 16
XL = XL ⊕Pi
XR = f(XL) ⊕XR
Swap XL, XR
(Undo last swap)
1. XR = XR ⊕P17
2. XL = XL ⊕P18
3. Concatenate XL and XR back into X to get ciphertext CT

DECRYPTION:



EXPERIMENTS CARRIED OUT

1. With small symmetric cipher key: REV
The blowfish_algo file is imported into the algo.py file and a symmetric cipher is assigned
to the algorithm. The message is not encrypted as this key is not between 4 to 56 bytes (32-
448 bits); enhanced security is achieved with longer key length. Displays an error message
that key is not accepted.


2. With min length symmetric cipher key: ISAA
The blowfish_algo file is imported into the algo.py file and a symmetric cipher is assigned
to the algorithm. The message is encrypted and this is the min length accepted by the
algorithm anyways this is not advisable as enhanced security is achieved with longer key
length. The encrypted message is displayed

3. With medium key length : ISAA_EMAIL_Cryptography_Blowfish_Algorithm
The blowfish_algo file is imported into the algo.py file and a symmetric cipher is assigned
to the algorithm. The key is of 42 bytes and the max length accepted is 56 hence the
message is encrypted.

4. With key exceeding maximum length :
Six_big_juicysteakssizzledinapanasfiveworkmen_leftthequarry
The blowfish_algo file is imported into the algo.py file and a symmetric cipher is assigned
to the algorithm. The key is 59 bytes and the max length accepted is 56 hence the message
is not encrypted. An error message is displayed.


##### Structure
```
.
├── algo.py
├── blowfish_algo.py
├── README.md
├── receive.py
└── send.py
```

##### File description
| File       | Description                                             |
|------------|---------------------------------------------------------|
| algo.py    | Methods to Encrypt and Decrypt using Blowfish algorithm |
| send.py    | Encrypt message and Send email                          |
| receive.py | Receive email and Decrypt message                       |

### Setup

##### Cipher key
`Admin key` is the symmetrical cipher key used by Blowfish algorithm for both Encryption and Decryption. Set a custom admin_key in the [algo.py](./algo.py) file.
```python
# Replace admin_key with string
# Size > 4 bytes
cipher = blowfish.Cipher(b"admin_key")
```
##### Testing
Testing Blowfish algorithm

```python
python algo.py
```
Must generate the following output
```
JuxX3vmzzDqblD/SZJyJ8PICXrVfzcBWZZBX6Kk=
Testing Blowfish: Success ✓
```
##### Email (Gmail)
###### Sending email
Replace values with sender Email ID and Password and receiver Email ID in the [send.py](./send.py) file.
```python
fromx = "anuhya@gmail.com"
to = "yourname@gmail.com"
password = "password"
```
[Additional Setup](https://www.lifewire.com/allow-email-programs-access-to-gmail-with-password-1171875) for sending email using Gmail.

###### Receiving email
Replace values with sender Email ID and Password [receive.py](./receive.py) file.
```python
user = 'anuhyareceiver@gmail.com'
password = 'password'
```
[Additional setup](https://www.geeksforgeeks.org/python-fetch-your-gmail-emails-from-a-particular-user/amp/) for receiving email from Gmail.

##### Run
```python
# Encryption message and
# Sending email
python send.py

# Receiving email and
# Decryption message
python receive.py
```

### Result
###### Encode and Send E-mail
```
Enter message to send: Testing email encryption using Blowfish algorithm.

Sending email ...
----------------------------
From:    example@gmail.com
To:      donjoe@gmail.com
Subject: ENC: Sample mail
Message:
 CCn4VdEuE33qHpW197H+5+sBTcKO/7vvIllr9eE4MGnx4cYlH8VISLAvBp3+fYEkoZk=
----------------------------

Message sent ...  ✓
```

###### Receive and Decode E-mail
```
Raw email content
-----------------------------
...
Subject: ENC: Sample mail
From: example@gmail.com
To: donjoe@gmail.com

CCn4VdEuE33qHpW197H+5+sBTcKO/7vvIllr9eE4MGnx4cYlH8VISLAvBp3+fYEkoZk=
-----------------------------

Encrypted message
CCn4VdEuE33qHpW197H+5+sBTcKO/7vvIllr9eE4MGnx4cYlH8VISLAvBp3+fYEkoZk=

Decrypting ...
Decrypted message ✓
Testing email encryption using Blowfish algorithm.
```