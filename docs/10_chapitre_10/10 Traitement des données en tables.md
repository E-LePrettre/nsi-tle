---
author: ELP
title: 10 Traitement des données en tables
---

**Table des matières** 

1. [**  AVEC LA BIBLIOTHEQUE CSV**](#_page0_x40.00_y360.92)
2. [**EXPLOITATION DES DONNEES AVEC LA BIBLIOTHEQUE CSV**](#_page7_x40.00_y36.92)
3. [**EXERCICES**](#_page12_x40.00_y36.92)
3. [**PROJET (DEMARCHE D’INVESTIGATION)**](#_page13_x40.00_y36.92)

## **1. Avec la bibliothèque csv<a name="_page0_x40.00_y360.92"></a>**

### **1.1. Les fichiers CSV** 

Une **table est une liste de p-uplets nommés** qui partagent les mêmes descripteurs (chaque champ de chaque p-uplet a le même nom). 

**Remarque** : Un fichier CSV est un fichier dans lequel il y a une table. **En général, la première ligne de la table correspond aux descripteurs**. Les lignes suivantes correspondent **aux données**. Les lignes sont séparées par le caractère \n (retour chariot). Chaque champ est séparé par **une tabulation, une virgule ou un point-virgule**. Le séparateur en France est **;** mais ce n'est pas le même dans d'autres pays, ni pour tous les logiciels (soyez vigilants)!  

Voici un exemple du contenu d'un fichier CSV : 
```CSV
Album;groupe;année;classement
Master of Puppets;Metalica;1986;1
Paranoid;Black Sabbath;1970;2
Rage against the machine;Rage against the machine;1992;3
Ride the lightning;Metallica;1984;4
Rust in peace;Megadeth;1990;5
Metallica;Metallica;1991;6
Toxicity;System of a down;2001;7
reign in blood;Slayer;1986;8
the number of the beast;Iron maiden;1982;9
From mars to sirius;Gojira;2005;10
..and justice for all;Metallica;1988;11
Mutter;Rammstein;2001;12
Painkiller;Judas Priest;1990;13
Powerslave;Iron maiden;1984;14
Blawater Park;Opeth;2001;15
```
 

Notez que la première ligne contient les noms de colonnes que l'on pourrait associer aux clés vues dans les dictionnaires.... On appelle ces noms les **descripteurs**. 

### **1.2. Ouvrir<a name="_page1_x40.00_y36.92"></a> un fichier CSV, le passer en table ou dictionnaire** 

On peut récupérer les données d'un fichier CSV dans un tableau doublement indexé : lignes, colonnes. Pour cela on utilise la **commande** reader de la bibliothèque csv qui retourne une **liste de listes.** 



**Activité n°1.: Création d’un fichier CSV** : Copier-coller le contenu de **la fenêtre ci-dessus** dans un fichier ouvert avec Notepad++, notepad, Excel, ou autre… et enregistrer le sous le nom musique.csv dans le dossier Documents. Une version du fichier se trouve dans Ressources
Le délimiteur dans ce fichier CSV est un point-virgule. 



**Activité n°2.: Lecture et création de liste puis de liste de listes avec un CSV (délimiteur ;)** : copier-coller et enregistrer le fichier python créé dans le dossier Documents précédent sous le nom de musique.py. Puis lancer le script. 
```python
import csv
table=[]
csv_fichier = open("musique.csv")       # ouvre le fichier CSV
csv_read = csv.reader(csv_fichier, delimiter=';')       # lit et précise le délimiteur
for row in csv_read:                                    # pour chaque ligne de csv_read
    print(row)                                  	 # affiche chaque ligne

    # pour construire la liste de liste
    table.append(row)                                   # construit la liste de liste
print("#############################################""")# decoration
print("la liste est : ",table)                          # affichage de la liste de liste
print("#############################################""")# decoration
print("1ère ligne :", table[0][0], ", 2ème colonne :",table[0][1])  # affiche l'élément
csv_fichier.close()
```


On peut alors facilement manipuler cette table puisque c'est **une liste de listes**.  



**Activité  n°3.:  Lecture  et  creation  de  liste  avec  un  fichier  CSV  (délimiteur ,)** :  Copier  le  fichier personnes.csv du dossier Ressources dans le dossier Documents. Puis copier-coller et enregistrer le fichier python créé dans le dossier Documents précédent sous le nom de personne.py. Puis lancer le script. 
```python
import csv
table=[]
csv_fichier = open("personnes.csv")                     # ouvre le fichier CSV
csv_read = csv.reader(csv_fichier, delimiter=',')       # lit et précise le délimiteur
for row in csv_read:                                    # pour chaque ligne de csv_read
    print("ligne : ",row)                               # affiche chaque ligne
    table.append(row) 				      # construit la liste de liste
print(table)                                                            
csv_fichier.close()
```




**Activité n°4.: Lecture et creation de dictionnaires avec un fichier CSV (délimiteur ,)** : copier-coller et enregistrer le fichier python créé dans le dossier Documents précédent sous le nom de personne_dico.py. 
Puis lancer le script. 
```python
import csv
csv_file = open('personnes.csv', "r")
reader = csv.DictReader(csv_file, delimiter=',')
for row in reader:
    print(dict(row))
csv_file.close()
```

**Autre méthode**, on récupère le fichier CSV dans une **liste de dictionnaires** qui ont tous les mêmes descripteurs avec la commande DictReader de la bibliothèque csv. 
A noter que DictReader crée une liste de dictionnaires ordonnés ! 

**Activité n°5.: Création de liste de dictionnaires** : copier-coller et enregistrer le fichier python créé dans le dossier Documents précédent sous le nom de musique_dico.py. Puis lancer le script. 
```python
import csv
dico=[]
csv_fichier = open("musique.csv")       # ouvre le fichier CSV
csv_read = csv.DictReader(csv_fichier, delimiter=';')   # lit convertit en dico précise le délimiteur

for row in csv_read:                                    # pour chaque ligne de csv_read
    print("ligne",row)                                  # affiche chaque ligne
    print(row['Album'])
    dico.append(row)                                    # construit la liste de dico
print("#############################################""")# decoration
print("le dico est : ",dico)                            # affichage de dico
print("#############################################""")# decoration
print("1ère ligne, 2ème colonne :",dico[0]['Album'])    # affiche l'élément
csv_fichier.close()
```




**Activité n°6.: Création de liste de dictionnaires v2**: copier-coller et enregistrer le fichier python créé dans Documents précédent sous le nom de personne_dico2.py. Puis lancer le script. 
```python
import csv
reader = csv.DictReader(open('personnes.csv', 'r',))
personnes = []
for row in reader:
    personnes.append(dict(row))

print(personnes)
```


**Activité n°7.: Création de liste de dictionnaires v3 encore plus court** : copier-coller et enregistrer le fichier python créé dans le Documents précédent sous le nom de personne_dico3.py. Puis lancer le script. 
```python
import csv
reader = csv.DictReader(open('personnes.csv', 'r'))
personnes = [dict(ligne) for ligne in reader]

print(personnes)
```

En créant une liste de dictionnaires qui possèdent les mêmes clés, on obtient une structure qui ressemble à une base de données.  

**Remarque** : un fichier JSON qui est un autre type de base de données peut également contenir une liste de dictionnaires. 



**Activité n°8.: Création de liste de dictionnaires sans le module** csv **de Python** : copier_coller et enregistrer le fichier python créé dans le Documents précédent sous le nom de personne_dico4.py. Puis lancer le script. 
```python
csv_file = open('personnes.csv', "r")
personnes = []
entetes = csv_file.readline().strip().split(',')

for ligne in csv_file:
    donnees = ligne.strip().split(',')
    personnes.append({entete: donnees[index] for index, entete in enumerate(entetes)})
csv_file.close()

print(personnes)
```

### **1.3. Enregistrer<a name="_page5_x40.00_y36.92"></a> un fichier CSV, ajouter une ligne** 

Tout comme précédemment, on peut enregistrer des tables dans un fichier CSV, ou une liste de dictionnaires. Il faudra veiller à la cohérence des données ! 


**Activité n°9.: Création d’un fichier csv à partir d’une liste et à partir d’une liste de tuples** : Copier-coller le script dans un fichier qui sera nommé creationCSV.py. Lancer le et observer le fichier creationstock.csv
Le fichier CSV contient :
```csv
Symbol;Prix;Date;Heure;Change;Vol
AB;30;6/2/2018;8:11am;-0.28;15500
KJL;55;6/2/2018;8:11am;-0.95;445500
MMP;88;6/2/2018;8:11am;-0.26;966000
```
```python
import csv
en_tetes = ['Symbol','Prix','Date','Heure','Change','Vol'] 	#liste
lignes = [('AB', 30, '6/2/2018', '8:11am', -0.28, 15500),
        ('KJL', 55, '6/2/2018', '8:11am', -0.95, 445500),
        ('MMP', 88, '6/2/2018', '8:11am', -0.26, 966000),
       ]                                                    	#liste de tuples

with open("creationstock.csv",'w') as stock:    # ouvre le fichier CSV
    stock_csv = csv.writer(stock,delimiter=';') # ouvre en écriture précision délimiteur
    stock_csv.writerow(en_tetes)                # écrit la liste en_tetes
    # extraction des tuples de la liste pour les mettre dans une nouvelle lists
    for symbol, prix, date, heure, change, vol in lignes: 
        table=[]
        table.append(symbol)
        table.append(prix)
        table.append(date)
        table.append(heure)
        table.append(change)
        table.append(vol)
        print(table)                        #affiche les tuples convertis en liste
        stock_csv.writerow(table)           #écrit les tuples extrait en converti en liste

stock.close()
```

**Activité n°10.: Création d’un fichier csv à partir d’une liste et à partir d’une liste de tuples** : Copier-coller le script dans un fichier qui sera nommé creationCSVversioncourte.py. Lancer et observer le fichier creationstockversioncourte.csv. Noter la difference de syntaxe entre une création d’un CSV à partir d’une liste ou d’une liste de tuples
Le fichier CSV contient :
```csv
Symbol;Prix;Date;Heure;Change;Vol
AB;30;6/2/2018;8:11am;-0.28;15500
KJL;55;6/2/2018;8:11am;-0.95;445500
MMP;88;6/2/2018;8:11am;-0.26;966000
``` 
```python
import csv
en_tetes = ['Symbol','Prix','Date','Heure','Change','Vol'] #liste
lignes = [('AB', 30, '6/2/2018', '8:11am', -0.28, 15500),
        ('KJL', 55, '6/2/2018', '8:11am', -0.95, 445500),
        ('MMP', 88, '6/2/2018', '8:11am', -0.26, 966000),
       ]                                                    #liste de tuple

stock = open("creationstockversioncourte.csv",'w') # ouvre le fichier CSV
stock_csv = csv.writer(stock,delimiter=';')     # ouvre en écriture précision délimiteur
stock_csv.writerow(en_tetes)                    # écrit la liste en_tetes
stock_csv.writerows(lignes)                     # écrit la liste des tuples versn supercourt
stock.close()
```

**Activité n°11.: Création d’un fichier csv à partir d’une séquence de dictionnaire** : à partir d’une liste et à partir d’une liste de dictionnaires. Copier-coller le script dans un fichier qui sera nommé creationCSVdico.py. 
Lancer le et observer le fichier creationstockdico.csv
Le fichier CSV contient :
```csv
Symbol;Prix;Date;Heure;Change;Vol
AB;30;6/2/2018;8:11am;-0.28;15500
KJL;55;6/2/2018;8:11am;-0.95;445500
MMP;88;6/2/2018;8:11am;-0.26;966000
``` 
```python
import csv
en_tetes = ['Symbol','Prix','Date','Heure','Change','Vol'] #liste
lignes = [{'Symbole':'HHA', 'Prix':350.48, 'Date':'6/1/2018',
          'Heure':'50:36am', 'Change':-0.58, 'Vol':585855},
        {'Symbole':'NNG', 'Prix': 75.38, 'Date':'6/1/2018',
          'Heure':'50:36am', 'Change':-0.55, 'Vol': 5505555},
        {'Symbole':'UOP', 'Prix': 62.58, 'Date':'6/1/2018',
          'Heure':'50:36am', 'Change':-0.46, 'Vol': 5035550},
        ]                                                       #liste de dictionnaire

with open("creationstockdico.csv",'w') as stock:                # ouvre le fichier CSV
    #il faut définir l'endroit de l'entete
    stock_csv = csv.DictWriter(stock,fieldnames=lignes[0].keys(),delimiter=';')
    stock_csv.writeheader()                                     # écrit la liste en_tetes
    for i in lignes:                                            #extraction des dicos
        stock_csv.writerow(i)                                   #ecrit les dico extraits
stock.close()
```

On a utilisé ici ```with``` qui permet seulement une plus grande clarté du code. **Les deux scripts sont totalement équivalents.** 

### **1.4. Fusion<a name="_page6_x79.00_y408.92"></a> de deux fichiers CSV** 

**Activité  n°12.:  Création  de  liste  de  dictionnaires à  partir  de  2  fichiers  CSV**  :  Copier  le  fichier transports.csv du dossier Ressources dans le  dossier Documents. Copier-coller et enregistrer le fichier python créé dans le dossier Documents précédent sous le nom de transports.py. Puis lancer le script. 
```python
import csv
reader = csv.DictReader(open('transports.csv', 'r',))
transports = []
for row in reader:
    transports.append(dict(row))

reader = csv.DictReader(open('personnes.csv', 'r',))
personnes = []
for row in reader:
    personnes.append(dict(row))

for i in range(len(personnes)):
    for v in [ vh for vh in transports if vh['age']==personnes[i]['age'] ]:
        personnes[i]['vehicule'] = v['vehicule']

print(personnes)
```


## **2.Exploitation<a name="_page7_x40.00_y36.92"></a> des données avec la bibliothèque csv**

On utilise un fichier nommé ‘countries.csv’ et ‘cities.csv’ contenant quelques données sur les différents pays et ville du monde. En voici les premières lignes pour countries.csv :  
```csv
ISO;Name;Capital_Id;Area;Population;Continent;Currency_Code;Currency_Name
AD;Andorra;3041563;468;84000;EU;EUR;Euro
AE;United Arab Emirates;292968;82880;4975593;AS;AED;Dirham
AF;Afghanistan;1138958;647500;29121286;AS;AFN;Afghani
AG;Antigua and Barbuda;3576022;443;86754;NA;XCD;Dollar
AI;Anguilla;3573374;102;13254;NA;XCD;Dollar
AL;Albania;3183875;28748;2986952;EU;ALL;Lek
```


**Remarques :** 

- Les champs sont clairement séparés par des **points-virgules.** 
- Comme c’est souvent le cas, la première ligne est utilisée pour indiquer le nom des différents champs : c’est **l’entête**. Dans ce cas, le premier enregistrement se trouve sur la deuxième ligne du fichier. 
- La signification des différents champs est transparente. A part le champ nommé Capital_Id dont les valeurs sont des numéros d’identifiants de villes que l’on trouvera dans le fichier nommé cities.csv. 

Les données sont issues du site[ http://www.geonames.org ](http://www.geonames.org/)

### **2.1. Importation<a name="_page7_x40.00_y304.92"></a> des données en liste de listes** 



**Activité n°13.: Importation des données** : Copier le fichier countries.csv dans le dossier Documents. Et copier coller le script suivant dans un fichier countries.py 
```python
import csv

pays = []
csvfile = open('countries.csv', newline='')   # Ouverture du fichier .csv
reader = csv.reader(csvfile, delimiter=';')  # Création d'un objet "lecteur", à itérer
for row in reader:
    pays.append(row)

csvfile.close()
```

Dans ce cas, les résultats sont stockés sous forme d’un tableau de tableaux (ou liste de listes au sens de Python). On peut ainsi obtenir la liste des noms des champs (ligne d’en-tête) : 
```python
print(pays[**0**]) 
```
ou le premier enregistrement : 
```python
print(pays[**1**]) 
```


Cette structure n’est pas la plus satisfaisante car le lien entre les valeurs du tableau pays[1]  et le nom des enregistrements, contenus dans pays[0] , n’est pas direct. 

### **2.2. Importation<a name="_page7_x40.00_y724.92"></a> des données en dictionnaire ordonné** 

La  fonction ```DictReader()```  de  da  bibliothèque csv   retourne  un  objet  DictReader   pour  chaque enregistrement, la première ligne étant utilisée pour nommer les différents champs. 


**Activité n°14.: Importation des données** : Copier coller le script suivant dans un fichier countriesdico.py 
```python
import csv

pays = []
with open('countries.csv', newline='') as csvfile:
    reader = csv.DictReader(csvfile, delimiter=';')  # Objet DictReader (itérateur)
    for row in reader:
        pays.append(dict(row))  # Conversion du type OrderedDict en dictionnaire

csvfile.close()        
print(pays[0])
```


**Remarque** : La conversion du *dictionnaire ordonné* en *dictionnaire* ```dict(row)``` permet uniquement d’avoir un affichage plus plaisant. 

Cette fois ci, on obtient un tableau de p-uplets représentés sous forme de dictionnaire. 

### **2.3. Interrogation<a name="_page8_x40.00_y305.92"></a> de la base de données** 

On peut traduire en Python des questions simples.  

**Activité n°15.: Question simple :** on peut poser la question : quels sont les pays où l’on paye en euro ? Ajouter à la place du ```print(pays[0])``` dans le fichier countriesdico.py le script suivant : 
```python
print([p['Name']for p in pays if p['Currency_Code'] =='EUR']) 
```

**Activité n°16.: A faire tout seul :** Écrire l’instruction permettant de lister les **codes (**Currency_Code**) de** **toutes les monnaies (**Currency_Name**) qui s’appellent ‘**Dollar**’**. 

> ```# ??```
```
['XCD', 'XCD', 'USD', 'AUD', 'BBD', 'BMD', 'BND', 'BSD', 'BZD', 'CAD', 'AUD', 'NZD', 'AUD', 'XCD', 'USD', 'FJD', 'USD', 'XCD', 'USD', 'GYD', 'HKD', 'JMD', 'AUD', 'XCD', 'KYD', 'XCD', 'LRD', 'USD', 'USD', 'XCD', 'NAD', 'AUD', 'AUD', 'NZD', 'NZD', 'NZD', 'USD', 'USD', 'SBD', 'SGD', 'SRD', 'USD', 'USD', 'USD', 'TTD', 'AUD', 'TWD', 'USD', 'XCD', 'USD', 'USD', 'ZWL']
```

On obtient une liste contenant beaucoup de doublons.  


**Activité n°17.: A faire tout seul : Pour les supprimer les doublons :** on convertit la liste en ensemble (set) avec la  fonction ```set()```  à  placer  devant  l’instruction.  Écrire  l’instruction  permettant  de  lister  les  **codes** (Currency_Code) de toutes les monnaies (Currency_Name) qui s’appellent ‘**Dollar**’** sans doublons 

> ```# ??``` 
```
{'TWD', 'CAD', 'BBD', 'BSD', 'TTD', 'SRD', 'BMD', 'SGD', 'BZD', 'XCD', 'JMD', 'NZD', 'KYD', 'HKD', 'BND', 'LRD', 'NAD', 'FJD', 'USD', 'ZWL', 'SBD', 'GYD', 'AUD'}
```



**Activité n°18.: A faire tout seul : Question plus difficile :** Écrire l’instruction permettant de lister les **noms des pays** (Name) **de plus de 100 millions d’habitants** (Population), sous la forme (Pays => Population (en Millions d’habitants)).  

Aide :```p['……']```  renvoie un string, il faut donc utiliser les fonction ```int()``` et ```str()```.  Arrondir à 2 avec la fonction ```round()```. On doit obtenir : 

> ```# ?? ```
```
['Bangladesh => 1.56', 'Brazil => 2.01', 'China => 13.3', 'Indonesia => 2.43', 'India => 11.73', 'Japan => 1.27', 'Mexico => 1.12', 'Nigeria => 1.54', 'Pakistan => 1.84', 'Russia => 1.41', 'United States => 3.1']
```

### **2.4. Tri<a name="_page9_x40.00_y140.92"></a>** 

Pour exploiter les données, il peut être intéressant de les trier. Une utilisation possible est l’obtention du classement des entrées selon tel ou tel critère. Une autre utilisation vient du fait que, comme présenté dans la partie algorithmique du programme, la **recherche dichotomique** dans un tableau trié est bien plus efficace que la recherche séquentielle dans un tableau quelconque. 

#### **2.4.1. Tri<a name="_page9_x40.00_y216.92"></a> selon un unique critère** 

On ne peut pas directement trier le tableau pays… car cela ne veut rien dire. Il faut indiquer selon quels critères on veut effectuer ce tri. 

Pour cela, on appelle la fonction ```sorted()```  ou la méthode ```.sort()``` , avec l’argument supplémentaire key  qui est une fonction renvoyant la valeur utilisée pour le tri. 

La  méthode ```.sort()```   trie  la liste en  place,  alors que  la fonction ```sorted()```  renvoie  une  nouvelle liste correspondant la liste triée, la liste initiale étant laissée intacte. 

**Activité n°19.:** Par exemple, si l’on veut trier les pays par leur superficie, on doit spécifier la clé Area . Pour cela, on définit une fonction appropriée (A ajouter à la suite du précédent fichier): 
```python
def cle_superficie(p):
   return p['Area']
```

Ainsi, pour classer les pays par superficie décroissante, on effectue (A ajouter à la suite du précédent fichier)
```python
pays.sort(key=cle_superficie, reverse=True) 
```

Mais un petit problème demeure. Si on récupère les noms des 5 premiers pays ainsi classés, le résultat est étonnant

> ```[(p['Name'], p['Area'])for p in pays[:5]]``` 

On ne s’attend pas à trouver la Corée du Sud parmi eux. La raison est que lors de l’import, tous les champs sont considérés comme des chaînes de caractères, et le tri utilise l’ordre du dictionnaire. Ainsi, de même que 'aa'  arrive avant 'b' , '10'  arrive avant '2' . Cela apparaît ici en regardant les superficies qui commencent par 998, puis par 984, par 962, etc. 

**Activité n°20.:** Pour remédier à cela, on modifie la fonction de clé : 
```python
def cle_superficie(p):
   return float(p['Area'])
pays.sort(key=cle_superficie, reverse=True)
```
> ```[(p['Name'], p['Area']) for p in sorted(pays, key=cle_superficie, reverse=True)[:5]]``` 

Ou plus simplement (sans la fonction cle_superficie) 

> ```sorted([(p['Name'], float(p['Area'])) for p in pays], key=lambda p:p[1], reverse=True)[:5]```


**Activité n°21.: A faire tout seul :** Écrire les instructions permettant d’afficher les **10 pays les moins peuplés**, dans l’**ordre croissant de leur population**, sous la forme **(pays, population)** 
Puis, **é**crire les instructions permettant d’afficher les **10 pays les moins peuplés**, dans l’**ordre inverse de leur** **population**, sous la forme **(pays, population)** 

> ```# ??```
```
ordre décroissant :
[('China', '1330044000'), ('India', '1173108018'), ('United States', '310232863'), ('Indonesia', '242968342'), ('Brazil', '201103330'), ('Pakistan', '184404791'), ('Bangladesh', '156118464'), ('Nigeria', '154000000'), ('Russia', '140702000'), ('Japan', '127288000')]
```

> ```# ??```
```
ordre croissant :
[('South Georgia and the South Sandwich Islands', '30'), ('Pitcairn', '46'), ('French Southern Territories', '140'), ('Cocos Islands', '628'), ('Vatican', '921'), ('Christmas Island', '1500'), ('Norfolk Island', '1828'), ('Niue', '2166'), ('Svalbard and Jan Mayen', '2550'), ('Falkland Islands', '2638')]
```


#### **2.4.2. Tri<a name="_page10_x40.00_y371.92"></a> selon plusieurs critères** 



**Activité n°22.: Trie à clé unique :** Supposons maintenant que l’on veut trier les pays selon deux critères : tout d’abord le *continent*, puis le *nom* *du pays*. On peut faire cela en définissant une fonction de clé qui renvoie une paire (*continent*, *nom du pays*) : 
```python
def cle_combinee(p):
   return (p['Continent'], p['Name'])
```

> ```[(p['Continent'], p['Name']) for p in sorted(pays, key=cle_combinee)]```



Cependant, dans ce tri, les deux critères ont été utilisés pour un ordre croissant.  

**Activité n°23.: Trie à double clé :** Supposons maintenant que l’on veuille trier les pays par *continent* et, pour chaque continent, avoir les pays par population décroissante. La méthode précédente n’est pas applicable, car on a utilisé une unique clé (composée de deux éléments) pour un tri croissant. 
À la place, nous allons procéder en deux étapes : 
1.  **trier tous les pays par populations décroissantes** ; 
2.  **trier ensuite le tableau obtenu par continents croissants**. 

```python
def cle_population(p):
    return int(p['Population'])

def cle_continent(p):
    return p['Continent']

pays.sort(key = cle_population, reverse = True)
pays.sort(key = cle_continent)
```

> ```[(p['Name'], p['Continent'], p['Population']) for p in pays]```


La fonction de tri de Python vérifie une propriété très importante : la **STABILITE**. Cela signifie que lors d’un tri, si plusieurs enregistrements ont la même clé, l’ordre initial des enregistrements est conservé. 

Ainsi, si on a trié les pays par ordre décroissant de population puis par continent, les pays d’un même continent seront regroupés en conservant l’ordre précédent, ici la population décroissante. 



**Activité n°24.: A faire tout seul :** Écrire les instructions permettant d’afficher les **8 pays possédant la plus grande densité de population**, dans l’**ordre inverse de densité**, sous la forme (Pays, densité).  

Aide : Se poser d’abord la question : comment calcule-t-on la densité ? On pourra également utiliser la fonction ```round()``` 

> ```# ??```
```
[('Nigeria', 'AF', '154000000'), ('Ethiopia', 'AF', '88013491'), ('Egypt', 'AF', '80471869'), ('Democratic Republic of the Congo', 'AF', '70916439'), ('South Africa', 'AF', '49000000'), ('Tanzania', 'AF', '41892895'), ('Kenya', 'AF', '40046566'), ('Sudan', 'AF', '35000000'), ('Algeria', 'AF', '34586184'), ('Morocco', 'AF', '33848242'), ('Uganda', 'AF', '33398682'), ('Ghana', 'AF', '24339838'), ('Mozambique', 'AF', '22061451'), ('Madagascar', 'AF', '21281844'), ('Ivory Coast', 'AF', '21058798'), ('Cameroon', 'AF', '19294149'), ('Burkina Faso', 'AF', '16241811'), ('Niger', 'AF', '15878271'), ('Malawi', 'AF', '15447500'), ('Mali', 'AF', '13796354'), ('Zambia', 'AF', '13460305'), ('Angola', 'AF', '13068161'), ('Zimbabwe', 'AF', 
…
```

Nous l’avons vu, il est assez facile d’écrire en Python des commandes simples pour exploiter un ensemble de données. Cependant, une utilisation plus poussée va vite donner lieu à des programmes fastidieux : notamment, pour pouvoir exploiter les capitales des pays, nous allons devoir utiliser des données présentes dans un fichier supplémentaire. Pour remédier à ce problème, on peut utiliser la bibliothèque pandas qui permet d’exprimer de façon simple, lisible et concise ce genre de manipulation de données. 

## **3. Exercices<a name="_page12_x40.00_y36.92"></a>** 

**Exercice 1** : **Sélection dans la Bibliothèque** 

![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.015.png)![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.016.png)

1. Donner une condition logique (pas en Python) sur la table *LIVRE* vraie pour tous les livres de *Kawabata* (et seulement eux) 
1. Donner une expression d’interrogation utilisant seulement l’opérateur de sélection pour calculer à partir de la table *LIVRE* la table répondant à la question : « Donner les livres de *Kawabata* (c’est-à-dire des lignes complètes de la table *LIVRE*) ». 
1. Ecrire un code Python qui calcule, à partir de la représentation Python de la table *LIVRE*, la représentation Python de la sélection de la question précédente, la place dans une variable, puis l’affiche (avec une deuxième boucle) 

**Exercice 2** : **Composition dans la Bibliothèque** 

![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.015.png)![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.016.png)

1. Donner une expression d’interrogation utilisant la composition des opérateurs de sélection et de projection pour calculer la table répondant à la question : « Donner les titres des livres de Kawabata ». 
1. Ecrire un code Python qui calcule la représentation Python de la table valeur de l’expression de la question précédente, comme suit. La sous-expression la plus interne est calculée et sa valeur est placée dans une variable. Puis l’expression englobante est calculée à partir de la table contenue dans cette variable. Sa table résultat est placée dans une nouvelle variable, puis affichée. 

**4.  Projet (démarche d’investigation)<a name="_page13_x40.00_y36.92"></a>** 

**Projet 1** : ★**  **pandy pandas pas à pas** 

On trouve énormément de données au format CSV sur internet. Une partie de ces données sont publiques, par exemple le site[ data.gouv.fr ](https://www.data.gouv.fr/fr/)récence un grand nombre de données publiques. Ces données sont librement réutilisables. 

Voici un exemple du contenu d'un fichier CSV : 
```CSV
nom,prenom,date_naissance
Durand,Jean-Pierre,23/05/1985
Dupont,Christophe,15/12/1967
Terta,Henry,12/06/1978
```


1. Donner les différentes valeurs du descripteur "date_naissance". 

**Les données structurées au format CSV** 

2 Afin de découvrir ce qu'est "l'open data", se rendre sur le site data.gouv.fr. En haut et à gauche de la page d’accueil, cliquer sur "Découvrez L’OpenData". Résumer en quelques lignes ce que vous aurez appris en lisant cette page.

3 Explorer pendant quelques minutes le site data.gouv.fr. Rechercher les données "Opérations coordonnées par les CROSS" à l'aide du moteur de recherche proposé par le site. 

Ces données sont au format CSV 

4 Après avoir téléchargé le fichier ident_pointVirgule.csv du dossier Ressources, ouvrir ce dernier à l'aide d'un tableur. 

Si par hasard le tableur ne gère pas correctement le fichier avec le séparateur "point-virgule", il y a une version "séparateur virgule" du fichier : ident_virgule.csv dans le dossier Ressources 

Dans la suite, garder toujours cet éventuel problème à l'esprit (surtout avec des données "made in France"). Résultat attendu : 

![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.018.png)

Les données sont bien "rangées" dans un tableau avec des lignes et des colonnes (voilà pourquoi on parle de données tabulaires). 

Il est possible de trouver sur le web des données beaucoup plus intéressantes à traiter que celles contenues dans le fichier "ident_pointVirgule.csv" (ou "ident_virgule.csv"). Par exemple, le site sql.sh, propose un fichier csv contenant des informations sur l'ensemble des communes françaises. 

5 Ouvrir le fichier ville_point_virgule.csv du dossier Ressources à l'aide d'un tableur (c’est une version légèrement modifiée de celle disponible sur le site sql.sh, dans laquelle des entêtes ont été ajoutées). En cas de problème avec le tableur, il y a une version "séparateur virgule" : ville_virgule.csv (attention le séparateur "décimal" est ici le point). 

On obtient 12 colonnes (et 36700 lignes si on ne compte pas l'entête !), voici la signification de ces colonnes : 

- dep : numéro de département 
- nom : nom de la commune 
- cp : code postal 
- nb_hab_2010 : nombre d'habitants en 2010 
- nb_hab_1999 : nombre d'habitants en 1999 
- nb_hab_2012 : nombre d'habitants en 2012 (approximatif) 
- dens : densité de la population (habitants par kilomètre carré) 
- surf : superficie de la commune en kilomètre carré 
- long : longitude 
- lat : latitude 
- alt_min : altitude minimale de la commune (il manque des données pour certains territoires d'outre-mer) 
- alt_max : altitude maximale de la commune (il manque des données pour certains territoires d'outre-mer) 

6 Déterminer l'altitude maximale et l'altitude minimale de votre commune, en utilisant les tris et les filtres 

**Le traitement des données structurées** 

7 Copier le fichier ident\_virgule.csv et le placer dans le dossier Documents  

![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.019.png)

8 Créer le fichier csv_pandas.py et saisir le code Python suivant :  
```python
import pandas

ident = pandas.read_csv("ident_virgule.csv")
print(ident)
```


Le code ci-dessus est très simple : 

- Avec la première ligne, import de la bibliothèque pandas afin de pouvoir l'utiliser 
- À la deuxième ligne, création d’une variable "ident" qui va contenir les données présentes dans le fichier "ident_virgule.csv"  
- La troisième ligne affiche les données contenues dans la variable "ident" rangées sous la forme d'un tableau, un peu comme ce que nous obtenions en ouvrant le fichier "ident_virgule.csv" avec un tableur. 

Une colonne a été ajoutée par rapport à ce que nous obtenions avec le tableur : 

Les  nombres  présents  dans  cette  colonne  sont  appelés  des  index. Chaque ligne du tableau a un index (première ligne :  index 0, deuxième ligne index 1...)   

Les  colonnes  possèdent  également  des  index,  dans  notre  exemple ces index correspondent au "nom" (index de la première colonne), au "prenom" (index de la deuxième colonne) et à "date_naissance" (index de la troisième colonne) 
![](Aimg.png)
En résumé : les lignes possèdent des index (0,1,2..), les colonnes possèdent aussi des index ("nom", "prenom", …). 

9 Il est possible de récupérer certaines données du tableau, par exemple, certaines lignes, certaines colonnes ou bien encore des valeurs uniques. Pour cela, il suffit d'utiliser l'instruction "loc" avec les index des lignes et les index des colonnes. Le principe de fonctionnement de "loc" est relativement simple puisque l'on aura une instruction de la forme "```loc[index_ligne,index_colonne]```" 
```python
import pandas

ident = pandas.read_csv("ident_virgule.csv")
print(ident)

info  = ident.loc[1, 'prenom']
print(info)
```
 

La variable "info" doit contenir le prénom "christophe". 

10 Modifier le programme pour que la variable info affiche "12/06/1978". 
11 Il  est  possible  de  récupérer  plusieurs  toutes  les  lignes  d'une  colonne,  il  suffit  de  remplacer  la  partie "index_ligne" de "loc" par ":" (pour faire un slicing): 
```python
import pandas

ident = pandas.read_csv("ident_virgule.csv")
info  = ident.loc[:, 'prenom']
```


Vérifier que la variable "info" contient bien toutes les données de la dernière ligne (index 2). 

12 Il est aussi possible de récupérer seulement certaines lignes et certaines colonnes en utilisant la notation suivante : ```loc[[index_ligne_1,index_ligne_2,...],[index_colonne_1,index_colonne_2,…]]``` : 
```python
import pandas

ident = pandas.read_csv("ident_virgule.csv")
info  = ident.loc[[0,1], ['nom','date_naissance']]
```


Vérifiez que la variable "info" contient bien un tableau avec uniquement les colonnes "nom" et "date_naissance" de la première ligne (index 0) et de la deuxième ligne (index 1). 

Afin d'avoir des exemples plus complexes à traiter, dans la suite, on travaille dans la suite sur les données contenues dans le fichier ville_virgule.csv. 

13 Tester le programme suivant : 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
```


Vérifier que la variable "info_villes" contient bien les données contenues dans le fichier ville_virgule.csv. Il manque des données dans le tableau qui s'affiche dans la console (les données manquantes sont symbolisées par des …). En effet, le tableau contient trop données pour qu'il soit entièrement affiché dans la console. 

En explorant le tableau, on devrait, notamment dans les colonnes l'altitude mini et maxi, voir apparaître un étrange "NaN" (Not a Number) pour les dernières villes du tableau car certaines données sont manquantes. 

Maintenant, pour obtenir un tableau contenant toutes les villes qui ont une altitude minimum supérieure à 1500 m, on va devoir introduire des conditions dans la sélection des villes. 

14 Tester le programme suivant : 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
nom_alt = info_villes.loc[info_villes["alt_min"] > 1500, ["nom","alt_min"]]
print(nom_alt)
```

Dans la fonction "loc", l'expression "```info_villes["alt_min"]>1500```" est bien avant la virgule, elle concerne donc les index des lignes du tableau. On sélectionnera uniquement les lignes qui auront la valeur du descripteur "alt_min" supérieure à 1500. Nous allons donc bien sélectionner les villes qui ont une altitude minimum supérieure à 1500 m. 

15 Écrire un programme qui permet d'avoir les villes qui ont une densité d'habitant inférieure à 50 (dans le tableau ainsi créé, on aura 3 colonnes : le nom de la ville, la densité de la population et l'altitude minimum) 
16 Il est possible de combiner plusieurs facteurs de sélection en utilisant un "et"("&") ou un "ou"("|") : 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
nom_alt = info_villes.loc[(info_villes["alt_min"] > 1500) \
    & (info_villes["dens"] > 50), ["nom","dens","alt_min"]]
print(nom_alt)
```


Il y a, en France, une seule ville avec une densité de population supérieure à 50 et une altitude minimum supérieure à 1500 m. Donner son nom. 

17 Il est aussi possible d'effectuer des calculs sur des colonnes, par exemple des moyennes. Il suffit d'utiliser l'instruction "mean" pour effectuer une moyenne : 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
moyenne_alt_min = info_villes.loc[:,"alt_min"].mean()
print(moyenne_alt_min)
```


L'altitude minimum moyenne est de 193 m en France.
 

On rappelle que dans "```loc[:,"alt\_min"]```" le ":" signifie que l'on considère toutes les lignes du tableau. De plus le "alt_min" que le calcul de la moyenne porte bien sur les données du descripteur "alt_min". 

18 Écrire un programme permettant de calculer le nombre moyen d'habitants en 2012 
19 Pour l'instant nous avons calculé une moyenne sur l'ensemble des lignes, il est aussi possible d'imposer une condition sur les lignes qui seront utilisées pour le calcul : 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
nombre_hab = info_villes.loc[info_villes["alt_min"] > 1500, \
    "nb_hab_2012"].mean()
print(nombre_hab)
```
 

On constate que les villes ayant une altitude minimum supérieure à 1500 m avaient en moyenne 350 habitants en 2012. 

20 Il est aussi possible de trier le tableau en fonction des valeurs d'un descripteur. Il suffit d'utiliser l'instruction "sort_values" : 
```python
import pandas
info_villes=pandas.read_csv("villes_virgule.csv")
tri_alt_min=info_villes.sort_values(by=["alt_min"])
```


On obtient un nouveau tableau de données "tri_alt_min" trié dans l'ordre croissant des altitudes minimums. Donner la ville ayant l'altitude minimum la plus faible de France. 

21 Il est aussi possible de trier par ordre décroissant en ajoutant "```ascending=False```" 
```python
import pandas

info_villes = pandas.read_csv("villes_virgule.csv")
tri_alt_min = info_villes.sort_values(by=["alt_min"], ascending=False)
print(tri_alt_min)
```


Indiquer la ville ayant l'altitude minimum la plus importante de France. 

22 Écrire un programme permettant de répondre à la question suivante de façon très facile : quelle est la ville ayant la densité de population la plus forte ? 

Il est possible de fusionner 2 tableaux de données qui ont une colonne commune. 

Afin  de  travailler  sur  cette  fusion,  nous  allons  utiliser  2  fichiers  au  format  CSV  : fiches_client.csv  et fiches_com.csv. 

23 Copier les 2 fichiers ci-dessus dans le dossier Documents, tester le code suivant : 
```python
import pandas

client = pandas.read_csv("fiches_client.csv")
commande = pandas.read_csv("fiches_com.csv")

print(client)
print("--")
print(print(commande))
```
 

Nous avons un tableau qui référence les clients (nom, prénom, ville), chaque client possède un numéro de client. Le deuxième tableau référence des commandes : pour chaque commande, nous avons un numéro de commande, une date et le numéro du client qui a passé la commande, ce numéro de client correspond évidemment au numéro de client que l'on trouve dans le premier tableau. 

24 Sachant que nous avons deux colonnes contenant les mêmes types d'information (numéros de client), nous allons pouvoir fusionner les deux tableaux en un seul : 
```python
import pandas

client = pandas.read_csv("fiches_client.csv")
commande = pandas.read_csv("fiches_com.csv")

cmde_client = pandas.merge(client, commande)
print(cmde_client)
```
 

Prenons l'exemple de Mme Julie Gabriaux qui habite à Bordeaux (n° de client 2454) et de la commande effectuée le 02/02/2012 par le client ayant le n° 2454 (commande n° 45). La cliente qui a passé cette commande n° 45 est bien Mme Gabriaux, nous avons une ligne dans notre tableau "cl-com" : 

![](Aimg2.png)

Nous avons bien fusionné les 2 tableaux "client" et "commande" en un seul tableau "cl_com" qui regroupe les informations pour chaque commande. Quand on effectue ce genre de fusion, on dit souvent que l'on effectue une jointure. 

25 Il faut prendre garde à l'ordre des arguments de la fonction "merge" : 
```python
import pandas

client = pandas.read_csv("fiches_client.csv")
commande = pandas.read_csv("fiches_com.csv")

cmde_client = pandas.merge(commande, client)
print(cmde_client)
```



Comme vous pouvez le constater, l'ordre des colonnes est différent. Il faudra donc être attentif à l'ordre des paramètres de la fonction "merge". 

26 Mme Élodie Gaulin (n° de client 895) bien que présente dans le tableau "client", est absente du tableau "com_cl" (ou "cl_com"). Dire pourquoi. 

27 De la même manière, aucun trace de la commande n° 1324 du 01/02/2017 dans le tableau "com_cl" (ou "cl_com"). Dire pourquoi. 

**Projet 2** : ★** ★  **Qualité de l’air** 

La ville de Digne, en association avec[ les petits débrouillards du 04 ](https://www.lespetitsdebrouillardspaca.org/-04-Alpes-de-Hautes-Provence-.html)a initié une campagne de  mesures de la qualité de l’air. Ces mesures sont issues des[ 4 stations ](http://umap.openstreetmap.fr/fr/map/capteurs-datadigne_131379#17/44.09167/6.23628)répartis dans le centre-ville de Digne-les-Bains. 

Les stations de qualité de l’air sont connectées et ont été réalisées par les élèves du Lycée Pierre Gilles de Gennes dans le cadre du projet [ Data'Digne.](https://www.dignelesbains.fr/2018/01/datadigne-concevoir-de-capteurs-de-mesure-de-la-qualite-de-lair/) Ces capteurs ont une vocation pédagogique et citoyenne sur la pollution atmosphérique. 

Le fichier fourni permet de connaître la concentration dans l’air des particules fines PM10, PM2.5 et PM1 ainsi que le taux d’humidité, la pression atmosphérique et la température sur une année. Le fichier est composé de 78 986 lignes. La mise à jour du fichier est annuelle, le fichier le plus récent remplace le précédent. 

Pour des mesures de qualité de l’air à vocation non pédagogique, rendez-vous sur[ https://www.atmosud.org/ ](https://www.atmosud.org/)

**Récupération dans un fichier d’une seule journée d’enregistrement** 

![](Aspose.Words.5d6a7bee-2757-45f8-93f7-fc7ecadeaafd.039.png)

On désire exploiter fichier des mesures 2018 fourni au format CSV. On  souhaite en particulier voir l’évolution des mesures sur la journée choisie  par  l’utilisateur,  conformément  au  graphe  ci-contre.  Pour  cela  on  va  décomposer le programme en fonctions élémentaires que l’on validera  avant de passer à la suite.  

On complétera le programme air_quality.py à l’aide de l’objet Python  csv.  

1. Copier le  fichier  des  mesures  2018  au  format  CSV  (Coma  Separated Values).  
2. L'enregistrer dans votre répertoire Documents  
3. Ouvrir le fichier et observer la manière dont est codée la date. 
4. Écrire une fonction qui enregistre uniquement les mesures sur une date précise dans un fichier CSV ayant comme  nom digne-année-mois-jour.csv,  où  année,  mois  et  jour  seront  saisies  interactivement  par l’utilisateur sous la forme jour/mois/année. 

On donne le prototype suivant : 

```create_daily_list(input_file : str, output_file : str, date : str) -> list```

- ```input_file``` -- fichier en entrée
- ```output_file ``` -- fichier en sortie
- ```date``` -- date pur filtrage de données
- la fonction retourne les enregistrements de la jouréne sélectionnée si OK ou None si erreur


**Aide** : 

- l’ouverture du fichier d’entrée utilisera la virgule comme delimiter 
- l’ouverture du fichier de sortie sera codée : 
```new_file = open(output_file, 'w', newline='', encoding='utf-8') ```



- la date sera entrée sous la forme ‘01/04/2018’. On pourra séparer le jour, le mois et l’année avec la méthode split('/')
- la même date peut apparaitre sur plusieurs lignes 
- attention la date sur le fichier CSV est notée 2018-04-01 et est contenu dans la colonne 1 donc pour pouvoir comparer la date entrée avec la date sur le fichier CSV il faut donc ne sélectionner que le début jusqu’à l’heure et changer l’affichage. On écrira : 

```if row[1].split(' ')[0] == year+"-"+month+"-"+day :```


NB : on utilisera les méthodes reader, writer et writerow de l’objet Python csv. 

5 Tester la fonction pour le 01/04/2018. 

Résultat attendu :

```
[['DataDigne.PS', '2018-04-01 00:01:49', '1.12', '0.0', '1.12', '50.93', '937.13', '8.08'],  ['DataDigne.HDV',  '2018-04-01  00:06:27',  '0.5',  '0.0',  '0.5',  '48.5', '935.01', '8.15'], ['DataDigne.CCRC', '2018-04-01 00:08:10', '0.0', '0.0', '0.0', '46.0', '935.9', '9.61'], ['DataDigne.PS', '201 ... 
```

6 Le tableau précédent ne contient pas de ligne d’entêtes. On va donc la rajouter  L’idée est de mettre une condition qui ne fonctionne qu’une seule fois pour la première ligne que l’on ajoutera à la liste puis la condition n’étant plus respectée on ajoute les autres lignes à la liste. 

7 Documenter la fonction 

**Création d’une liste de valeurs classées par heures, sur une journée** 

8 ★** ★** ★**  On veut écrire une fonction qui renvoie une liste de mesures pour chaque heure. Chaque liste contient les valeurs mesurées correspondant à une colonne (un type de mesure) pour l’heure concernée. Le prototype de la fonction est le suivant : 

```create_hourly_values_list(output_file : str, colunm : str) -> list```
- ```output_file``` -- fichier en sortie (fonction précédente fichier CSV déjà sélectionné par jour) 
- ```colunm``` -- entête de colonne pour sélectionner la mesure souhaitée 
- la  fonction  retourne  une  liste  contenant  24  listes  (une  pour  chaque  heure)  avec  les  mesures correspondantes (par exemple la température) si ok, ou None si erreur 

Résultat attendu avec la température  
```
[[8.08, 8.15, 9.61, 7.92, 8.17, 9.35, 7.33, 7.83, 9.57, 7.48, 7.54, 10.0, 7.49, 7.53, 9.59, 7.18, 7.41, 9.74], [7.04, 6.95, 9.0, 6.76, 6.9, 9.73, 6.5, 6.67, 9.3, 6.26, 6.66, 9.28, 6.46, 6.54, 9.05, 6.53, 6.7, 8.83], [6.19, 6.55, 9.01, 6.16, 6.04, 8.4, 6.13, 6.01, 8.77, 5.79, 6.05, 8.25, 6.12, 6.2, 8.26, 5.77, 6.37, 8.08], [5.69, 6.49, 8.24, 6.48, 5.98, 8.14, 5.91, 6.28, 8.43, 6.23, 6.39, 7.85, 6.14, 6.42, 8.3, 6.01, 6.13, 6.8], [6.29, 5.79, 6.59, 5.49, 5.43, 5.72, 5.82, 5.31, 5.93, 5.72, 5.44,… 
```
**Aide** : 

- on utilisera la même méthode que précédemment pour mettre la ligne d’en-tête sur la liste  
- pour récupérer l’heure  

```hour, min, sec = row[1].split(' ')[1].split(':') ```

- on créera une liste de 24 listes vides à l’aide de la compréhension de liste. 
- Si vous avez converti les mesures en float, comme c’est souhaitable, une erreur apparaît car certains champs sont vides. D’autres peuvent contenir tout autre chose. 
- Traiter les problèmes de conversion à l’aide d’une exception. 

La fonction est déjà créée au-dessus si vous n’y arrivez pas copier là en dessous de la fonction create_daily_list

**Création d’une liste de valeurs horaires moyenne pour une journée** 

On souhaite obtenir la valeurs moyenne des mesures heure par heure. Pour cela, on va écrire une fonction qui prend en paramètre la liste retournée par la fonction create_hourly_values_list. Pour rappel, cette liste contient 24 listes, chacune des listes contient les valeurs de mesures pour une heure donnée. 

9 ★** ★** Écrire la fonction dont on donne le prototype : 

```create_hourly_averages_list(hourly_values_list : list) -> list```

- ```hourly_values_list``` -- liste de 24 listes contenant chacune les valeurs numériques (de type float) pour l'heure concernée 

- la fonction retourne la liste des 24 moyennes horaires 

**Aide :**  

- Pour limiter l’impact des erreurs de mesures, on souhaite supprimer au préalable la valeur min et la valeur max de la liste des mesures effectuées chaque heure. 
- on pourra appeler une fonction interne qui effectue ce calcul avec les fonctions built_in de Python (sum, max et min). 

10 Documenter la fonction 

**Affichage des données** 

11 Ecrire un script qui permet de demander à l’utilisateur une date et qui retourne la moyenne par heure de cette date de « TEMPERATURE » en combinant les fonctions précédentes 

On  veut  afficher  l’évolution  des  valeurs  journalières  sous  forme  de  graphe  avec  matlibplot. [https://matplotlib.org/3.1.0/tutorials/index.html ](https://matplotlib.org/3.1.0/tutorials/index.html)

12 Appeler la fonction ```show_plot()``` pour afficher les valeurs moyennes des températures sur 24 h.  



**Projet 3** : ★** Pokémon 

