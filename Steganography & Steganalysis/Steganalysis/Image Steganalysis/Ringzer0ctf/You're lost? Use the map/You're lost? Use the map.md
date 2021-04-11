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
![tree](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/tree.png)

### __1ère tentative__
On nous propose de télécharger le fichier joint que je m'empresse de faire avec l'outil wget.
![wget](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/wget.png)


Dans le monde Unix/Linux, la notion d'extension n'existe "presque" pas. Le type d'un fichier est uniquement déterminé par son 'magic number'.
De ce fait, bien que l'extension soit ici .zip, il se pourrait qu'il n'en soit pas un en réalité. Je vais donc à la pêche aux infos.



Cette analyse montre que le fichier n'est pas une archive mais plutôt un texte ASCII que je me presse de lire avec un éditeur ASCII !



Nous avons en face de nous une suite binaire qui semble être un message comme le laisse croire la classe "message" de la balise div. 
Ce message binaire converti en texte ASCII par l'outil en ligne https://cryptii.com/pipes/binary-to-text nous dis que nous faisons fausse route.  


**Prise de recul** / **Conclusion**: 
Nous avons pris ce râteau parce que le fichier .zip à télécharger est placé derrière une protection d'authentifiction. 
Le concepteur de l'exercice a d'ailleurs été gentil de nous laisser un message clair à ce propos. D'où la deuxième tentative.


### __2ème tentative__
Maintenant que nous avons apris de nos erreurs, nous pouvons soit téléchargé directement en cliquant sur le bouton proposé soit utilisé l'outil wget comme suit:
```console
root@intrusion:~$ wget --http-user=USERNAME --http-password=PASSWORD http://SOMETURLTOFILE
```
![file xxd](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/file%20xxd.png)

![file xxd](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/unzip%20file%20eog.png)

![flag](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/flag.png)

> Flag  
J'ai soumis ces combinaisons de flags  
flag-hsdf83ksk22  
FLAG-HSDF83KSK22  
hsdf83ksk22   
