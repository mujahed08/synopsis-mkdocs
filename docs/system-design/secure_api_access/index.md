# How to secure API acess for you APIs.

1. Token based authentication
2. HMAC (Hash-based Message Authentication Code) authentication

## HMAC (Hash-based Message Authentication Code) authentication

HMAC authentication is used when integrity of data (request payload) to be ensure from being attacked during the message transmission.

It uses symmetric key for creating hash at client side and verifying the hash at server side.

**Explore:** Elliptic Curve Digital Signature Algorithm