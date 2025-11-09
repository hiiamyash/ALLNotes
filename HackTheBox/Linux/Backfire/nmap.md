
ORT     STATE SERVICE  REASON         VERSION
22/tcp   open  ssh      syn-ack ttl 63 OpenSSH 9.2p1 Debian 2+deb12u4 (protocol 2.0)
| ssh-hostkey: 
|   256 7d:6b:ba:b6:25:48:77:ac:3a:a2:ef:ae:f5:1d:98:c4 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBJuxaL9aCVxiQGLRxQPezW3dkgouskvb/BcBJR16VYjHElq7F8C2ByzUTNr0OMeiwft8X5vJaD9GBqoEul4D1QE=
|   256 be:f3:27:9e:c6:d6:29:27:7b:98:18:91:4e:97:25:99 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIA2oT7Hn4aUiSdg4vO9rJIbVSVKcOVKozd838ZStpwj8
443/tcp  open  ssl/http syn-ack ttl 63 nginx 1.22.1
|_ssl-date: TLS randomness does not represent time
| ssl-cert: Subject: commonName=127.0.0.1/organizationName=inc/stateOrProvinceName=California/countryName=US/streetAddress=/postalCode=7792/localityName=Los Angeles
| Subject Alternative Name: IP Address:127.0.0.1
| Issuer: commonName=127.0.0.1/organizationName=inc/stateOrProvinceName=California/countryName=US/streetAddress=/postalCode=7792/localityName=Los Angeles
| Public Key type: rsa
| Public Key bits: 2048
| Signature Algorithm: sha256WithRSAEncryption
| Not valid before: 2024-05-25T07:45:55
| Not valid after:  2027-05-25T07:45:55
| MD5:   cfd1:09c9:f535:d2bc:53c6:1747:6c2a:5280
| SHA-1: 64d0:19d3:71e9:77ef:b520:f88e:7167:5808:cc16:18c2
| -----BEGIN CERTIFICATE-----
| MIID5DCCAsygAwIBAgIQAsYDU5NjlXjQMlOxtABVpDANBgkqhkiG9w0BAQsFADB0
| MQswCQYDVQQGEwJVUzETMBEGA1UECBMKQ2FsaWZvcm5pYTEUMBIGA1UEBxMLTG9z
| IEFuZ2VsZXMxCTAHBgNVBAkTADENMAsGA1UEERMENzc5MjEMMAoGA1UEChMDaW5j
| MRIwEAYDVQQDEwkxMjcuMC4wLjEwHhcNMjQwNTI1MDc0NTU1WhcNMjcwNTI1MDc0
| NTU1WjB0MQswCQYDVQQGEwJVUzETMBEGA1UECBMKQ2FsaWZvcm5pYTEUMBIGA1UE
| BxMLTG9zIEFuZ2VsZXMxCTAHBgNVBAkTADENMAsGA1UEERMENzc5MjEMMAoGA1UE
| ChMDaW5jMRIwEAYDVQQDEwkxMjcuMC4wLjEwggEiMA0GCSqGSIb3DQEBAQUAA4IB
| DwAwggEKAoIBAQDFDYm6P9qqfC/v1GhdPJm8wCPChUfkhUut1t4c3mcTklBIMFV3
| Jn6BGUhUNFDUKM7unoLwH/SZDpa1zzpyWSAt8Qb2IoE6+idlikSLwd6Dic6vEL+k
| VVlhBBTfbI7HxUikRT0XnLw8Z8qWwOO+HNyoSvMjnhz/GVltRBi/cfG/YKZF7i3m
| rR5Zb3pT8gzWQqcpyO+07I9qU5CcrmJjS3gGZ0Ka6ngoIvNaImHPb9oLb/wxZy9E
| Z/jkTn3EdXFghDLQHWO5FMAm5SfZQj8WSSxA0bnqI16Mx6ylabj1/HF1uFig8PBr
| 1Hs7gI15MEcPRAj8SL+8LKBaG4qabGEUwXvvAgMBAAGjcjBwMA4GA1UdDwEB/wQE
| AwICpDAdBgNVHSUEFjAUBggrBgEFBQcDAQYIKwYBBQUHAwIwDwYDVR0TAQH/BAUw
| AwEB/zAdBgNVHQ4EFgQUobyQNhZk3FTW0FOroB60nrLhjFIwDwYDVR0RBAgwBocE
| fwAAATANBgkqhkiG9w0BAQsFAAOCAQEACGPfpSJG7sOFWW/1clHlBTw1vs1naEkl
| Gzqc9WVHJ/VymbnquPCCQ0yjb2oKgyP76ORsYrBXGoMeB9/MdLAzowFly6QTQFoT
| KPFnzmT2lId0s+6JZamuJP2zInonparCsPttxiy9oiNVzcLWfEfCblZ2bMqiY3qV
| T924bWqq42GfEJ6gxX7GAJA7meFIblEmlhGpo2TtHpx6KxEmR9wum+lGJsSHow5E
| ckaJwB/DEe6FFSaqZncSqEvJ4nhwbF0yUxoQROYvnnhQp8OFqkBvYt8Z+FwvF5LB
| ZYkDB++KfEnHvm7nXm0O1yIjLQxS54hct9Jufum9mOSQXJKlYMTB7Q==
|_-----END CERTIFICATE-----
|_http-server-header: nginx/1.22.1
|_http-title: 404 Not Found
| tls-alpn: 
|   http/1.1
|   http/1.0
|_  http/0.9
8000/tcp open  http     syn-ack ttl 63 nginx 1.22.1
|_http-title: Index of /
| http-methods: 
|_  Supported Methods: GET HEAD POST
|_http-open-proxy: Proxy might be redirecting requests
|_http-server-header: nginx/1.22.1
| http-ls: Volume /
| SIZE  TIME               FILENAME
| 1559  17-Dec-2024 11:31  disable_tls.patch
| 875   17-Dec-2024 11:34  havoc.yaotl



