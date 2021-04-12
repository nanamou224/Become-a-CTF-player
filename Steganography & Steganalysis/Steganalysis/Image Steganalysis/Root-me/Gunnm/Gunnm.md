## Informations du challenge
- Lien: https://www.root-me.org/fr/Challenges/Steganographie/Gunnm
- Titre: Gunnm
- Description: Une image pour commencer  
- [Fichiers du challenge](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/ch1.png)


## Outils et références utilisées
- La description 
- Les yeux
- La patience
- Utilitaires: wget, file, xxd, head, tail, unzip, eog


## Solution commentée
### Préparations 
Pour une meilleure organisation, nous créeons un repertoire portant le nom de l'exercice dans lequel nous mettons tous les fichiers afférents.
![tree](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/tree.png)

### __1ère tentative__
On nous propose de télécharger le fichier joint que je m'empresse de faire avec l'outil wget.
![wget](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/wget%20ls.png)


Dans le monde Unix/Linux, la notion d'extension n'existe "presque" pas. Le type d'un fichier est uniquement déterminé par son 'magic number'.
De ce fait, bien que l'extension soit ici .zip, il se pourrait qu'il n'en soit pas un en réalité. Nous allons donc à la pêche aux infos.
![file xxd head tail](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/file%20xxd%20head%20tail.png)


A ce niveau, le zoom-in s'avère fructueux en souvenir du descriptif du challenge [`Gunnm`](https://en.wikipedia.org/wiki/Battle_Angel_Alita) qui est une série qui se déroule dans un futur post-apocalyptique et se concentre sur le personnage Alita et boom ... le flag!
![flag](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/flag.png)

**Prise de recul** : 
1- Nous avons pu télécharger le fichier du challenge avec wget sans s'authentifier
2- On a pu se balader un tout petit peu sur le serveur (IDOR)



#### Flag  
Ayant deux mots, nous allons soumettre différentes combinaisons.   
>  PASS=TOTORO  
>  pass=totoro  
>  TOTORO

Finalement, flag="`TOTORO`"
