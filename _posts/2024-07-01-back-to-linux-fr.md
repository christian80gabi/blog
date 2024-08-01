---
title: "Retour à Linux : Mon Voyage d'Aller-Retour"
categories:
  - Blog
  - Linux
  - English
tags:
  - Linux
  - Open Source
  - openSUSE
  - Windows
header:
  image: /assets/images/2024-07-01/back_to_linux_1.png              # Twitter (use 'overlay_image')
  teaser: /assets/images/2024-07-01/back_to_linux_5.png   # Shrink image to 575x216
  caption: "Back to Linux: created with Bing Creator"
---


Salut ! Je suis de retour sur Linux. Eh oui, après seulement une semaine sous Windows, j'ai décidé de revenir à ma _"Loving affair"_. Vous vous demandez sûrement pourquoi ce revirement soudain. Permettez-moi de vous expliquer.

### Pourquoi j'avais quitté Linux pour Windows

Il y a une semaine (depuis cet [article](https://christian80gabi.github.io/blog/blog/linux/english/my-year-with-linux/)), j'avais fait le grand saut vers Windows pour plusieurs raisons, principalement :

- **Problèmes de connexion WiFi** : Mon adaptateur WiFi (RTL8822BE PCI) ne fonctionnait pas correctement sous Linux, et je n'avais pas trouvé de solution à ce problème à ce moment-là.
- **Expérience de jeu médiocre** : En tant que "casual gamer", il était frustrant de voir que certains jeux, conçus principalement pour Windows, ne fonctionnaient pas de manière optimale sous Linux, même avec des solutions comme Wine ou Proton via Steam.

### Pourquoi je suis revenu à Linux

Mais pourquoi revenir si vite à Linux ? La réponse est simple : **l'univers de la liberté**. Linux offre une transparence, un contrôle total sur son appareil, et une personnalisation sans limite de l'interface graphique. Toutes ces choses me manquaient.

### Problèmes sur Windows

De plus, ma semaine sur Windows n'a pas été de tout repos. Un incident majeur a précipité mon retour : je ne pouvais plus m'authentifier sur ma session. Pas une histoire de mot de passe oublié, mais plutôt un bug inexplicable qui m'empêchait d'accéder à mon bureau. Frustré, j'ai décidé de redonner une chance à Linux, tout en continuant à l'utiliser depuis un disque externe.

### Explorations sous Linux

Durant cette période, j'ai exploré différentes distributions Linux : Manjaro, Fedora, et même Arch Linux. Arch Linux, en particulier, a été une révélation. Il m'a permis de comprendre que mon problème de WiFi venait du "Active-State Power Management". Les drivers sous Linux peuvent réduire la puissance pour économiser l'énergie. En désactivant le mode "powersave" pour ma carte WiFi, j'ai enfin pu me connecter au réseau. Un autre obstacle s'est présenté : mon réseau domestique ne fonctionnait toujours pas. Après quelques recherches, j'ai remplacé le bon vieux "wpa_supplicant" par "iwd", une solution plus moderne, et tout fonctionnait parfaitement.

#### Désactiver "powersave" pour ma carte WIFI

Source : [Red Hat Docs](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/power_management_guide/aspm#ASPM)

> Il suffirait juste d'ajouter des options dans systemd-boot or GRUB pour une exécution lors du démarrage de Linux (kernel)


#### Changer de wpa_supplicant to iwd

    Install iwd
    
    sudo apt update
    sudo apt install iwd

    Create this file inside your NetworkManager configuration files directory

    sudo vim /etc/NetworkManager/conf.d/wifi_backend.conf

    Copy and paste into this file the following content, then save the file:

    [device]
    wifi.backend=iwd

    Stop and disable the wpa_supplicant service (note that disabling it is persistent after reboots)

    systemctl stop wpa_supplicant.service
    systemctl disable wpa_supplicant.service

    Enable and start iwd service (note that enabling it is persistent after reboots)

    sudo systemctl enable iwd.service
    sudo systemctl start iwd.service

    Restart NetworkManager service (this means you don't have to restart your computer for this to take effect--it just works immediately!)

    systemctl restart network-manager.service

    Now try to connect to the 2.4GHz wifi access point

Référence : [Arch Wiki](https://wiki.archlinux.org/title/NetworkManager#Using_iwd_as_the_Wi-Fi_backend)


### Solution pour le Gaming

Quant à mes soucis de gaming, j'ai trouvé une solution pratique : "Windows To Go". En installant Windows 11 sur un disque dur externe, je peux facilement alterner entre Linux et Windows selon mes besoins. J'ai également stocké mes jeux Steam et Epic Games sur un autre disque externe, ce qui me permet de jouer aussi bien sous Linux qu'avec Windows sans souci.

### Conclusion

En conclusion, ce retour à Linux, en particulier à OpenSUSE Tumbleweed, m'a permis de retrouver le plaisir d'une expérience informatique sur mesure. Pour les jeux Windows, "Windows To Go" et le stockage externe des jeux se sont avérés être des solutions efficaces. Si vous avez des questions ou des suggestions, n'hésitez pas à les partager !
