## Informations du challenge
- Lien: Merci à [Eliphélé AGOSSOU](https://twitter.com/charliagossou) pour la mise à disposition. Consultez ses writeups sur son [Github repository](https://github.com/CharliGithub/CTF) 
- Titre: Shit
- Description: Néant  
- [Fichiers du challenge](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Image%20Steganalysis/Root-me/Gunnm/Ressources/ch1.png)
- Niveau de difficulté: 101


## Outils et références utilisées
- La patience
- Google
- Utilitaires: file, xxd, head, tail, binwlak, unzip, tree, cat


## Solution commentée
### Préparations 
Comme d'habitude, nous créeons un repertoire portant le nom de l'exercice dans lequel nous mettons tous les fichiers afférents.
![tree cd](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/File%20Steganalysis/HackerLab2019/Shit/Ressources/mkdir%20cd.png)

### Analyse du fichier fourni
Nous commençons par déterminer le type de fichier. En effet, deux types de métadonnées permettent d'indiquer le format d'un fichier :  
- les métadonnées externes (il s'agit de l’extension du nom de fichier ou comme pour les type MIME)  
- les métadonnées internes (il s'agit des magic numbers)  

Vous l'aurez compris, nous allons nous fier uniquement qu'aux métadonnées internes dans la suite. 

![file xxd head tail](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/File%20Steganalysis/HackerLab2019/Shit/Ressources/file%20xxd.png)

Cette première analyse nous indique que le fichier est un Microsoft Excel 2007+.   
Par ailleurs, son magic number `504b0340` est générique avec zip, jar et presque toutes extensions de document de chez Microsoft.   
Pour donc démêler le vrai du faux, nous lançons une analyse statistique qui se base sur des signatures connues afin de déteter le type le plus probable et bim bam boum nous avons affaire à une archive `.zip`.

![binwalk B](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/File%20Steganalysis/HackerLab2019/Shit/Ressources/binwalk.png)


### Une étape de plus ...
A présent, nous savons que le fichier n'est pas anodin. Cherchons à savoir ce qui se cache derrière. 
- Méthode 1: Extraire les fichiers cachés avec binwalk   
![binwalk e](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/File%20Steganalysis/HackerLab2019/Shit/Ressources/binwalk%20tree.png)

- Méthode 2: Extraire les fichiers cachés avec unzip  
![unzip tree cat](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/File%20Steganalysis/HackerLab2019/Shit/Ressources/unzip%20tree%20cat.png)


#### Flag   
En fouillant dans tous les fichiers, on retrouve finalement le flag sur ce chemin: `xl/sharedStrings.xml`  
flag="`CTF_thaiq0H_ze8Hoow`"  

