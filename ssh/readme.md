# SSH

## SSH key management

### 🔑 The Key Pair Basics

- Public key: You upload this to your EC2 server (goes into ~/.ssh/authorized_keys for your user).
- Private key: You keep this locally on your computer. Never share it.

### ⚙️ What Happens During SSH Authentication

- You initiate SSH: You try to connect to the EC2 server with ssh -i private_key.pem ec2-user@server-ip.

- Server challenge: The EC2 SSH server sees your username, looks up the matching public key in its authorized_keys.

- Cryptographic challenge-response: The server does not ask you to send your private key. Instead, the server generates a random challenge (a piece of data) and encrypts it with your public key.

- Client proves identity: Your SSH client uses your private key to decrypt/sign that challenge.

- If the client produces the correct response, the server knows you hold the correct private key (without ever seeing it).

- Connection established:If the check passes, authentication succeeds and the session starts.If not, the server denies access.
