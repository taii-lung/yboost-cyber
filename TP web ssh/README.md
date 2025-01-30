### configurer une 2ème carte réseau
'''
tai_lung@serveurw:/var/www/html$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:0f:d3:4a brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 metric 100 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 84843sec preferred_lft 84843sec
    inet6 fe80::a00:27ff:fe0f:d34a/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 08:00:27:2e:ec:be brd ff:ff:ff:ff:ff:ff
    inet 192.168.56.106/24 brd 192.168.56.255 scope global dynamic noprefixroute enp0s8
       valid_lft 540sec preferred_lft 465sec
    inet6 fe80::a00:27ff:fe2e:ecbe/64 scope link
       valid_lft forever preferred_lft forever
'''

### creer un dossier html avec le code fourni 
'''
tai_lung@serveurw:/var/www/html$ cat index.html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YBOOST 1ère SEANCE</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            font-family: 'Arial', sans-serif;
        }

        .container {
            text-align: center;
        }

        .animated-title {
            font-size: 4rem;
            color: #ff6600;
            animation: fadeIn 2s ease-in-out;
            opacity: 0;
        }

        @keyframes fadeIn {
            0% {
                opacity: 0;
                transform: translateY(-50px);
            }
            100% {
                opacity: 1;
                transform: translateY(0);
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <h1 class="animated-title">YBOOST 1ère SEANCE</h1>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const title = document.querySelector('.animated-title');
            setTimeout(() => {
                title.style.opacity = '1';
            }, 500);
        });
    </script>
</body>
</html>
'''


### n'autoriser que les ports 22 et 80
'''
tai_lung@serveurw:/var/www/html$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere
22/tcp                     ALLOW       Anywhere
80/tcp (v6)                ALLOW       Anywhere (v6)
22/tcp (v6)                ALLOW       Anywhere (v6)
'''