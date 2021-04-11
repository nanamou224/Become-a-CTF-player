## Informations du challenge
- Lien: https://ringzer0ctf.com/challenges/118
- Titre: You're lost? Use the map
- Description: 


## Outils et références utilisées
- La description 
- Les yeux
- La patience
- Utilitaires: file, xxd, head, tail, unzip, gimp


## Solution détaillée
### Préparations 
Pour une meilleure organisation, nous créeons un dossier portant le nom de l'exercice dans lequel nous mettons tous les fichiers afférents.


### __1ère tentative__
On nous propose de télécharger le fichier joint que je m'empresse de faire avec l'outil wget.
```console
┌──(root💀intrusion)-[~/Desktop/CTF/Ringzer0ctf/You're lost? Use the map]
└─# wget https://ringzer0ctf.com/challenges/118
--2021-04-11 14:16:50--  https://ringzer0ctf.com/challenges/118
Resolving ringzer0ctf.com (ringzer0ctf.com)... 195.157.4.130, 195.157.4.140, 212.82.233.130, ...
Connecting to ringzer0ctf.com (ringzer0ctf.com)|195.157.4.130|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: /login [following]
--2021-04-11 14:16:51--  https://ringzer0ctf.com/login
Reusing existing connection to ringzer0ctf.com:443.
HTTP request sent, awaiting response... 200 OK
Length: 23645 (23K) [text/html]
Saving to: ‘118’

118                        100%[=======================================>]  23.09K  --.-KB/s    in 0.003s  

2021-04-11 14:16:51 (7.53 MB/s) - ‘118’ saved [23645/23645]

```

Dans le monde Unix/Linux, la notion d'extension n'existe "presque" pas. Le type d'un fichier est uniquement déterminé par son 'magic number'.
De ce fait, bien que l'extension soit ici .zip, il se pourrait qu'il n'en soit pas un en réalité. Je vais donc à la pêche aux infos.



Cette analyse montre que le fichier n'est pas une archive mais plutôt un texte ASCII que je me presse de lire avec un éditeur ASCII !



Nous avons en face de nous une suite binaire qui semble être un message comme le laisse croire la classe "message" de la balise div. 
Ce message binaire converti en texte ASCII par l'outil en ligne https://cryptii.com/pipes/binary-to-text nous dis que nous faisons fausse route.  


Prise de recul / Conclusion : 
Nous avons pris ce râteau parce que le fichier .zip à télécharger est placé derrière une protection d'authentifiction. 
Le concepteur de l'exercice a d'ailleurs été gentil de nous laisser un message clair à ce propos. D'où la deuxième tentative.


### __2ème tentative__
Maintenant que nous avons apris de nos erreurs, nous pouvons soit téléchargé directement en cliquant sur le bouton proposé soit utilisé l'outil wget comme suit:
```console
root@intrusion:~$ wget --http-user=USERNAME --http-password=PASSWORD http://SOMETURLTOFILE
```


> Flag
J'ai soumis ces combinaisons de flags  
flag-hsdf83ksk22  
FLAG-HSDF83KSK22  
hsdf83ksk22   
