# Secure Email Attachment Encryption with OpenSSL

Secure email attachment encryption using OpenSSL and 4096-bit RSA public-key cryptography to protect sensitive data during transmission.

This project demonstrates a secure workflow for sending sensitive files as encrypted email attachments in a corporate environment. The recipient generates an RSA key pair and shares the public key with the sender. The sender encrypts the file using the recipient’s public key, ensuring that only the intended recipient can decrypt the attachment using their private key.

Tools and technologies used include OpenSSL, RSA public-key cryptography (4096-bit), Windows command line tools, and a virtualized lab environment.

Workflow:
1. Generate a 4096-bit RSA private key for the recipient
2. Extract the corresponding RSA public key
3. Share the public key with the sender
4. Encrypt the sensitive attachment using the recipient’s public key
5. Transfer the encrypted file (simulated email attachment)
6. Decrypt the file using the recipient’s private key

OpenSSL commands used in this project:

Generate a 4096-bit RSA private key:
openssl genrsa -out pasha_private.pem 4096

Extract the RSA public key:
openssl rsa -in pasha_private.pem -pubout -out pasha_public.pem

Encrypt the attachment using the recipient’s public key:
openssl rsautl -encrypt -pubin -inkey pasha_public.pem -in creditCardInfo.txt -out creditCardInfoEncrypted.txt

Decrypt the attachment using the recipient’s private key:
openssl rsautl -decrypt -inkey pasha_private.pem -in creditCardInfoEncrypted.txt -out creditCardInfo.txt

Security concepts demonstrated include public-key encryption, secure key management, encryption of sensitive data prior to transmission, and ensuring confidentiality so only the intended recipient can access protected information.

No real sensitive data or private keys are included in this repository. In real-world environments, RSA is commonly used as part of a hybrid encryption model to securely exchange symmetric keys for encrypting large files.
