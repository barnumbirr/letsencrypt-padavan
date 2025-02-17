# letsencrypt-padavan

Let's Encrypt certificates for padavan / rt-n56u devices.

## Installation

Clone the repository and copy/edit the config file to fit your setup:

```bash
$ cd /opt/
$ git clone https://github.com/barnumbirr/letsencrypt-padavan.git
$ cd letsencrypt-padavan
$ cp sample.conf my.conf
```

## Usage

Pass all parameters to `letsencrypt-padavan`:

```bash
$ /opt/letsencrypt-padavan/bin/letsencrypt-padavan -u root -p 22 -k /opt/letsencrypt-padavan/id_ed25519 -h 10.0.1.253 -h 10.0.1.254 -d abc.yourdomain.com

[✱] About to deploy "/etc/letsencrypt/live/abc.yourdomain.com/cert.pem:"
        Subject: CN = abc.yourdomain.com
        Not Before: Nov 28 09:19:32 2021 GMT
        Not After : Feb 26 09:19:31 2022 GMT
        RSA Public-Key: (4096 bit)
        DNS:abc.yourdomain.com, DNS:xyz.yourdomain.com

[✓] Connection to device (10.0.1.253) successful!
        ____     root@ap1
       (.. |     os: GNU/Linux
       (<> |     kernel: 3.4.113
      / __  \    uptime: 90d16h8m
     ( /  \ /|   cpu: MediaTek MT7621 SoC (4 cores)
    _/\ __)/_)   memory: 21/256MB
    \/-____\/    shell: "/bin/sh"
[✱] Uploading certificate...
[✱] [▓▓▓▓]
[✓] Certificate uploaded successfully.
[✱] Uploading key...
[✱] [▓▓▓▓]
[✓] Certificate key uploaded successfully.
[✓] httpd restarted successfully! Device should now be accessible over HTTPS.

[✓] Connection to device (10.0.1.254) successful!
        ____     root@ap2
       (.. |     os: GNU/Linux
       (<> |     kernel: 3.4.113
      / __  \    uptime: 31d23h8m
     ( /  \ /|   cpu: MediaTek MT7621 SoC (4 cores)
    _/\ __)/_)   memory: 21/256MB
    \/-____\/    shell: "/bin/sh"
[✱] Uploading certificate...
[✱] [▓▓▓▓]
[✓] Certificate uploaded successfully.
[✱] Uploading key...
[✱] [▓▓▓▓]
[✓] Certificate key uploaded successfully.
[✓] httpd restarted successfully! Device should now be accessible over HTTPS.

$
```

Use the config file:

```bash
$ /opt/letsencrypt-padavan/bin/letsencrypt-padavan -c /opt/letsencrypt-padavan/my.conf
```

## Configuration reference

| Variable            | Example value                       | Description                                                                                                                                                                            |
| ------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PADAVAN_USER        | root                                | Specifies user used to connect to the device. (see `Advanced Settings > Administration > System > System Identification > Administrator Login`)                                        |
| PADAVAN_SSH_PORT    | 22                                  | Specifies SSH port used to connect to device. (enable SSH service under `Advanced Settings > Administration > Services > Terminal Services > Enable SSH Server`)                       |
| PADAVAN_PRIVATE_KEY | /opt/letsencrypt-padavan/id_ed25519 | Specifies private SSH key used to connect to device. (set under `Advanced Settings > Administration > Services > Terminal Services > SSH Public Authorization Keys (authorized_keys)`) |
| PADAVAN_HOSTS       | 10.0.1.1                            | Specifies IP address(es) used to connect to device.                                                                                                                                    |
| DOMAIN              | abc.yourdomain.com                  | Specifies first domain used by certbot to generate the certificate.                                                                                                                    |

## License:

```
Copyright 2021-2025 Martin Simon

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Buy me a coffee?

If you feel like buying me a coffee (or a beer?), donations are welcome:

```
BTC : bc1qq04jnuqqavpccfptmddqjkg7cuspy3new4sxq9
DOGE: DRBkryyau5CMxpBzVmrBAjK6dVdMZSBsuS
ETH : 0x2238A11856428b72E80D70Be8666729497059d95
LTC : MQwXsBrArLRHQzwQZAjJPNrxGS1uNDDKX6
```
