# Base64 Encoding

_Challenge_: get the username and password from base64 encoding `dXNlcm5hbWU6cGFzc3dvcmQ=`.

_Solution_: go to `https://www.base64decode.org/` and enter the base64 encoding.

Username is `username` and password is `password`.

# XOR Encoding

_Challenge_: get the password encoded as `{xor}Oz4rPj0+LDovPiwsKDAtOw==`.

_Solution_: search for IBM Xor Decoder (`https://strelitzia.net/wasXORdecoder/wasXORdecoder.html`) and enter the encoded password.

Password is `databasepassword`.

# Plain hashing

_Challenge_: get the password form hash `5F4DCC3B5AA765D61D8327DEB882CF99` and `2BB80D537B1DA3E38BD30361AA855686BDE0EACD7162FEF6A25FE97BF527A25B`.

_Solution_: go to `https://crackstation.net/` to reverse hash using a lookup table.

Passwords are `password` and `secret`.

# RSA Signature

_Challenge_: determine the modulus of the following RSA key as a hex string, and calculate a signature for that hex string using the key.

```
-----BEGIN PRIVATE KEY-----
MIIEvAIBADANBgkqhkiG9w0BAQEFAASCBKYwggSiAgEAAoIBAQC16sMVyQb/HeSYHdaAr9Au+qCaW5Wv8UUTKU6VpwS9OmcPSxRuyTBG70sY4XcQGVw3Y7Oigrl6X9c0AWi2coTsmEGoR9jTfzvOruTsCmiNS1r6ZugQoMdXCEznLbQmcVmIqgeCQyjRR8HX2rheew7owzTbJpcyuhBI3cxZ4YTVsb3MgjtXofeKsqkN2Wze93/xpMY9XZzlhAnQTe+OBbRe2GpGdjl0IOwGlPP8JGpqb3mxq7UlrdOqM2da4ECI+SlTFpcqPTVvm/guccI7gymo38SoKhxR3gPLt1ToYNvIhdvocPqPpszcvCr6jKKHnbXck6aO4gEKcyJJKw3GeVqhAgERAoIBACAaXql91A7nKFcUUwemjiZodrHT7T0qk7gWWSl306jsME3+MMhBnxuTo9c22MabEEYCiRytqELFnnKW1j5Qcc9mKbRI6gc0khVqKGXjuBjvLiwwRxH+QUuYDZI1Peiql1RaPY91Q3A51unbTbZR85J8zRedZfnkmXZFQi36nviIekR1926aNSiRSIPL2CLyrBABRcNQxdEArQ7K1peHWfiW3Ij+CA4RzL+JE5DBml0oasZoJOziZPv32Snltu7srfxbmqFOMH/GN94qIlSjBlucJWAlHO830W5RMxsA95z5VGkYkHCZr6lghI914xkcpYLtwx6LHVAIEY89S+ol8QECgYEAvFEv3T6v3WMbF6kSzfWD70kKqCBBsFy7DXRU5RTJca5/7W0Ltov3bOdx03bEIEEOFrx8CwqREyJckmNSO544QXC2fpeA8KLQDn1Uc9GVvj40ux4Hb9Zkv8TV+wjkhOTpAaLKgpWs5iZ/PD9Z+me3xrRGIYqMDc50TOjaqu1Vz0UCgYEA90y14/uIQkG1oSSY1iNpwaM9kspSNj3FJ7LQ9R6Smi+sRdEgVUMZ9uHFBvvB327RsJDhg4dvLvQFBl94TaDZDfcDrFYBMfi+AnDZNopRnLjg4GlQXdqSS+sVOEZ2279tUUdwmtE9rfZvVOOWoTxDmpe03gHsTSEmcd9KX1T3Na0CgYEAsT1aOaRpSNW/JVPVdoy4aL03NNMQpfzsSOX1jE/MpzrSwVeSjbDo3vfyqOhAHltYjd6S3TcfIRFIEU5rg2e8edN+lUNMLcZpdwyLuEzJK4XXRrLZ0quqHeZvCmK49YwmmCC+mQVXbzNKkw5yzY7LFV5gH5F0wbNASGKvr+5u4TECgYArpCAZLGNW/Il2yjkWuvSLlUcZ53frdE/38mEcMpJXcdMbYSPSz5srkUDjHV5yuTQQGZE1VCKt7tO11JzCZ63VSbVapcP5wnviUCZU6zuUIKAnmh09vSjgOItGKo1yErjwOciTypJp/k/hzc9JoTkbR/K9xBqkMwbIzQ0f4dFFtQKBgQC6tRJpfvsD5HsBa28xLth6/skZpCnbGMtlU3IKHO2h/Vi1kX7Hwu6W9I05l/rvwf0kuGRbSFL6WzW2KhPb0oXvglIfitDaZRdypcR6p6nNbxGDu07dDMP2yOAPWp4NHbOqrZMaajU0UIfILckaLhrtbI5CEImhyF9o7DmbEzjpwg==
-----END PRIVATE KEY-----
```

_Solution_: save the text to `private.key`.

```
openssl rsa -in private.key -modulus -noout -out modulus.txt
```

Edit `modulus.txt` and remove `Modulus=` at the start of the content.

```
echo -n $(cat modulus.txt) | openssl dgst -sha256 -sign private.key | openssl base64
```

Modulus:

```
B5EAC315C906FF1DE4981DD680AFD02EFAA09A5B95AFF14513294E95A704BD3A670F4B146EC93046EF4B18E17710195C3763B3A282B97A5FD7340168B67284EC9841A847D8D37F3BCEAEE4EC0A688D4B5AFA66E810A0C757084CE72DB426715988AA07824328D147C1D7DAB85E7B0EE8C334DB269732BA1048DDCC59E184D5B1BDCC823B57A1F78AB2A90DD96CDEF77FF1A4C63D5D9CE58409D04DEF8E05B45ED86A4676397420EC0694F3FC246A6A6F79B1ABB525ADD3AA33675AE04088F9295316972A3D356F9BF82E71C23B8329A8DFC4A82A1C51DE03CBB754E860DBC885DBE870FA8FA6CCDCBC2AFA8CA2879DB5DC93A68EE2010A7322492B0DC6795AA1
```

Signature:

```
CND3E+jMTaPCGQcTQknQ8j8u8h9UmT1XiKydyyS/nuAWLWWYtTIdpdObWjeWoeep Svjlwbg6nOu1h3BN1m5caF9CaP0jXJhVw0vdoPGT3GSwZizVt7SI7BIV8L5iKAtD GLikaZWjiTrcEKzdo0mt+Y5P9TdLdNgtNkf49QNeJajurtcAkkpqOKgOLPI0FIRw G0Crt03ITKE1fbXCR29FH0BW85crcDsVAa9ZqytW84O1ewBn41UN4skTf1H4Vb93 wJRNuYT+cwPIPiP0ex4cLiAl8UY9pcag6rAiHwbfwj6cxp2R5P9YskubYQG1UE9d p+WHh9cUpZectiL7Ujgwcw==
```

# Docker assignment

_Challenge_: retrieve a secret that has accidentally been left inside a docker container image. With this secret, you can decrypt the following message: `U2FsdGVkX199jgh5oANElFdtCxIEvdEvciLi+v+5loE+VCuy6Ii0b+5byb5DXp32RPmT02Ek1pf55ctQN+DHbwCPiVRfFQamDmbHBUpD7as=`

```
docker run -d webgoat/assignments:findthesecret
docker container ls
docker cp <id>:/etc/passwd ./
chmod a+w ./passwd
```

Edit `passwd` locally and change `webgoat:x:0:0::/home/webgoat:` to `webgoat:x:0:0::/home/webgoat:`.

```
docker cp ./passwd <id>:/etc/passwd
docker exec -ti <id> /bin/bash
ls root
echo "U2FsdGVkX199jgh5oANElFdtCxIEvdEvciLi+v+5loE+VCuy6Ii0b+5byb5DXp32RPmT02Ek1pf55ctQN+DHbwCPiVRfFQamDmbHBUpD7as=" | openssl enc -aes-256-cbc -d -a -kfile /root/default_secret
```

Unencrypted message is `Leaving passwords in docker images is not so secure` and the name of the file storing the password is `default_secret`.
