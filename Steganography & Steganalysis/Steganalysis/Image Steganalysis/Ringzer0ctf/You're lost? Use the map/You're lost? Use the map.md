## Informations du challenge
- Lien: https://ringzer0ctf.com/challenges/118
- Titre: You're lost? Use the map
- Description: 


## Outils et références utilisées
- La description 
- Les yeux
- La patience
- Utilitaires: file, xxd, head, tail, unzip, eog


## Solution commentée
### Préparations 
Pour une meilleure organisation, nous créeons un repertoire portant le nom de l'exercice dans lequel nous mettons tous les fichiers afférents.
![tree](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/tree.png)

### __1ère tentative__
On nous propose de télécharger le fichier joint que je m'empresse de faire avec l'outil wget.
![wget](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/wget.png)


Dans le monde Unix/Linux, la notion d'extension n'existe "presque" pas. Le type d'un fichier est uniquement déterminé par son 'magic number'.
De ce fait, bien que l'extension soit ici .zip, il se pourrait qu'il n'en soit pas un en réalité. Nous allons donc à la pêche aux infos.
![file xxd head tail](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/file%20xxd%20head%20tail.png)

Cette analyse montre que le fichier n'est pas une archive mais plutôt un texte ASCII que je me presse de lire avec un éditeur ASCII !
Nous voilà en face d'une suite binaire qui semble être un message comme le laisse croire la classe "message" de la balise div. 
Ce message binaire converti en texte ASCII par l'outil en ligne https://cryptii.com/pipes/binary-to-text nous dis que nous faisons fausse route.  
![binary2ascii](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/binary2ascii.png)



**Prise de recul** / **Conclusion**: 
Nous avons pris ce râteau parce que le fichier .zip à télécharger est placé derrière une protection d'authentifiction. 
Le concepteur de l'exercice a d'ailleurs été gentil de nous laisser un message clair à ce propos. D'où la deuxième tentative.  



### __2ème tentative__
Maintenant que nous avons appris de nos erreurs, nous pouvons soit télécharger directement en cliquant sur le bouton proposé soit utiliser l'outil wget comme suit:
```console
root@intrusion:~$ wget --http-user=ton_username_ici --http-password=ton_password_ici https://ringzer0ctf.com/files/a892385285c917f18f0f942457b90c0a.zip
```

Nous reprennons nos bonnes habitudes de chasse aux informations comme précédemment.

![file xxd](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/file%20xxd.png)

![file xxd](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/unzip%20file%20eog.png)

A ce niveau, le zoom-in s'avère fructueux en souvenir du descriptif du challenge et boom ... le flag!
![flag](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Ringzer0ctf/You're%20lost%3F%20Use%20the%20map/Ressources/flag.png)

#### Flag  
Ayant deux mots, nous allons soumettre différentes combinaisons.   
>  flag-hsdf83ksk22  
>  FLAG-HSDF83KSK22  
>  hsdf83ksk22   
>  flaghsdf83ksk22 

Finalement, flag="`flaghsdf83ksk22`"
