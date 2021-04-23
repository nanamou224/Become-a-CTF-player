## Informations du challenge
- Lien: https://ringzer0ctf.com/challenges/70
- Titre: Victor you're hidding me something  
- Description: Aucune
- [Fichiers du challenge](https://github.com/nanamou224/Become-a-CTF-player/blob/main/Steganography%20%26%20Steganalysis/Steganalysis/Text%20Steganalysis/Ringzer0ctf/Victor%20you're%20hidding%20me%20something/Ressources/poeme.txt)
- Niveau de difficulté: 101


## Outils et références utilisées
- Les yeux (l'attention)
- Expression regulière
- Utilitaires: cat, grep, cut, tr, grep


## Solution commentée 
Nous avons affaire à un beau texte poétique composé de 7 [strophes](https://fr.wikipedia.org/wiki/Strophe) ... quoique un peu bancal !  
Nous remarquons tout de suite que les premières lettres de la première strophe forment le mot-clé `FLAG`.
### Hypothèse :   
Les 6 dernières strophes respectent la même structure. Ce qui nous permet de conclure que le flag est constitué, dans cet ordre, des premières lettres de chaque [vers](https://fr.vikidia.org/wiki/Vers).  
- Méthode 1: Extraction manuelle  
Il suffit de noter dans un bloc note les premières lettres de chacun des vers : F, L, A, G, C, M, P, H, D, D, S, Q, N, U, C, C, P, N, N, S, O, Q, A, C, J, O, O et P.  Toutefois, cela peut vite être fastidieux dans le cas où le texte est long, d'où la méthode 2.  
- Méthode 2: Extraction automatique
Nous commençons par enegistrer le poème dans un fichier (ici `poeme.txt`). Ci-dessous deux commandes permettant de les extraire  
`cat poeme.txt | cut -c-1 | tr -d '\n'`  
`grep -Po '^.' poeme.txt | tr -d '\n'`  


#### Flag  
Nous allons soumettre différentes combinaisons   
>  FLAG CMPHDDSQNUCCPNNSOQACJOOP 
>  FLAG{CMPHDDSQNUCCPNNSOQACJOOP}  
>  FLAG_CMPHDDSQNUCCPNNSOQACJOOP   
>  FLAGCMPHDDSQNUCCPNNSOQACJOOP 

Finalement, flag="`FLAGCMPHDDSQNUCCPNNSOQACJOOP`"
