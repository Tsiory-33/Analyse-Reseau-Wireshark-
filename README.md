# 🛡️ Audit de Vulnérabilité Réseau : HTTP vs HTTPS

## 📝 Présentation du Projet
Ceci est un projet d'audit technique pour démontrer les risques d'interception de données sur un réseau non sécurisé. 
L'objectif est de comparer le comportement des protocoles HTTP (en clair) et HTTPS/TLS (chiffré) à l'aide de l'analyseur de paquets Wireshark.

## 🛠️ Environnement Technique
* OS : GNU/Linux Debian 12 (Bookworm)
* Outil d'analyse : Wireshark 4.0.x
* Cibles : neverssl.com (HTTP) et google.com (HTTPS)

## 🔍 Analyse Comparative

### 1. Flux HTTP (Non sécurisé)
Lors de l'analyse d'une session HTTP, j'ai utilisé la fonction "Follow HTTP Stream" de Wireshark. 
* Constat : L'intégralité du code HTML et des en-têtes (User-Agent, Host) est lisible en clair.
* Risque : Une attaque de type Man-in-the-Middle (MitM) permettrait à un tiers de voler des identifiants ou des cookies de session.

![Application d'un filtre : HTTP ](images/001.jpg)
![Ouverture d'un site sur le naviguateur : http://neverssl.com](images/002.jpg)
![Requete envoyé par le PC pour la demande du page](images/003.jpg)
![Follow -> Flux HTTP](images/004.jpg)

### 2. Flux HTTPS avec TLS (Sécurisé)
En répétant l'opération sur un site sécurisé, j'ai filtré le trafic via le protocole tls.
* Constat : Les données sont encapsulées. Le contenu est totalement chiffré et illisible sans la clé de déchiffrement.
* Résultat : Confidentialité et intégrité des données garanties par le protocole TLS.

![Application d'un filtre : TLS ](images/005.jpg)
![Ouverture d'un site sur le naviguateur : https://www.google.com](images/006.jpg)
![Requete envoyé par le PC pour la demande du page](images/007.jpg)
![Follow -> Flux TCP](images/008.jpg)
![Follow -> Flux TLS](images/009.jpg)

## 🚀 Conclusion
Ce projet démontre que l'implémentation de TLS n'est pas seulement une recommandation, mais une nécessité absolue pour toute application manipulant des données sensibles. J'ai pu valider techniquement le processus d'encapsulation des données et l'importance du chiffrement dans la protection de la vie privée.
entation de TLS n'est pas seulement une recommandation, mais une nécessité absolue pour toute application manipulant des données sensibles. J'ai pu valider techniquement le processus d'encapsulation des données et l'imp
