# KyberCloak
An encryption algorithm that is designed to be quantum attack proof
KyberCloak is an end-to-end encryption scheme that provides confidentiality, integrity, and authentication using AES, Kyber, and RSA algorithms.

## Features

- Encryption using AES-256 in CTR mode for confidentiality 
- Integrity protection using RSA-PSS signature with SHA-256
- Authentication using Kyber public key infrastructure
- Resists replay attacks using a random nonce 


### Encryption

To encrypt:

```python
from kybercloak import Encryptor

kyber_priv_key = b"<private_key>"
aes_key = b"<32_byte_key>" 
aes_iv = os.urandom(16)

encryptor = Encryptor(kyber_priv_key, aes_key, aes_iv)
ciphertext = encryptor.encrypt(plaintext) 
```

This will generate a nonce, encrypt using AES-CTR, sign the ciphertext, and return the payload.

### Decryption

To decrypt:

```python
from kybercloak import Decryptor

kyber_pub_key = b"<public_key>"
aes_key = b"<32_byte_key>"
aes_iv = os.urandom(16) 

decryptor = Decryptor(kyber_pub_key, aes_key, aes_iv)
plaintext = decryptor.decrypt(ciphertext)
```

This will verify the signature, decrypt the ciphertext, and return the plaintext.

## Security Considerations

- Use a cryptographically secure random number generator for keys and IVs.
- Keep private keys safe and secure - do not share these!
- Use at least 2048-bit RSA keys and 256-bit elliptic curve keys.
- Properly validate public keys to avoid MITM attacks.

## Contributors

KyberCloak was designed and implemented by Richard Aragon.

## License

MIT License - see `LICENSE` file.
