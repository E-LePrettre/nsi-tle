---
author: ELP
title: 12 Algorithme de Boyer - Moore
---



📚 **Table des matières**

[1.	Les fonctions déjà implémentées dans python	](#_toc159537143)

[2.	La recherche textuelle naïve](#_toc159537146)

[3.	Application de l’algorithme de Boyer-Moore](#_toc159537151)



🎯 **Compétences évaluables**

- Etudier l’algorithme de Boyer-Moore pour la recherche d’un motif dans un texte



---


## <H2 STYLE="COLOR:BLUE;"> <a name="_toc159537143"></a>**🪅 1. Les fonctions déjà implémentées dans Python**</H2>

!!! info "🧠 **Capytale : Le code vous sera fourni par votre enseignant**"

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537144"></a>**🎲 1.1. La méthode `index()`**</H3>

La méthode `index()` permet de rechercher une **sous-chaîne** dans une chaîne de caractères.

* Elle renvoie l’**indice de la première occurrence**
* Elle **lève une exception `ValueError`** si la sous-chaîne n’est pas trouvée

Exemple :

```python
texte = "Bonjour tout le monde"

print(texte.index("tout"))   # 7
print(texte.index("pomme"))  # ValueError
```

---

???+ question "🧠 **Activité n°1 — Utiliser la méthode `index()`**"
    👉 Écrire une fonction `trouve_lettre(c, texte)` qui :

    * renvoie l’indice de la **première occurrence** de `c` dans `texte`

    * renvoie `None` si la lettre n’est pas présente

    📌 **Indice** : utiliser `try / except`

    ```python
    def trouve_lettre(c, texte):
        """Renvoie l'indice de la première occurrence de c dans texte
        ou None si la lettre n'est pas trouvée"""
        pass

    assert trouve_lettre('j', 'bonjour') == 3
    assert trouve_lettre('j', 'alphabet') is None
    ```

    ??? success "✅ Solution"

        ```python
        def trouve_lettre(c, texte):
            try:
                return texte.index(c)
            except ValueError:
                return None

        assert trouve_lettre('j', 'bonjour') == 3
        assert trouve_lettre('j', 'alphabet') is None
        ```

---

#### 🔎 Vocabulaire essentiel

* **Motif** : chaîne de caractères recherchée

* **Occurrence** : position `i` telle que

  ```python
  texte[i:i+len(motif)] == motif
  ```

➡️ La recherche devient plus complexe lorsqu’on cherche un **motif** plutôt qu’un seul caractère.

---

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537145"></a>**🛡️ 1.2. La méthode `find()`**</H3>

Contrairement à `index()` :

* `find()` **ne lève pas d’exception**

* elle renvoie `-1` si le motif n’est pas trouvé

Exemple :

```python
texte = "Bonjour tout le monde"

print(texte.find("tout"))    # 7
print(texte.find("pomme"))   # -1
```

---

???+ question "🧠 **Activité n°2 — Recherche dans un texte long**"
    📖 Télécharger le roman *Le Rouge et le Noir* :

    🔗 [https://www.gutenberg.org/ebooks/798.txt.utf-8](https://www.gutenberg.org/ebooks/798.txt.utf-8)

    ➡️ Renommer le fichier : `rougenoir.txt`

    👉 Vérifier :

    * si le motif **"Julien"** apparaît dans le texte

    * trouver une **deuxième occurrence**

    ```python
    fichier = open('rougenoir.txt', 'r', encoding='utf-8')
    stendhal = fichier.read()
    fichier.close()

    print(stendhal.find('Julien'))
    print(stendhal.find('Julien', 25378))
    ```

    ??? success "✅ Solution"

        * Le premier `find` renvoie l’indice de la **première occurrence**

        * Le second permet de rechercher **après une position donnée**, donc une autre occurrence

---

???+ question "🧠 **Activité n°3 — Compter les occurrences**"
    👉 Compléter la fonction `nb_occurrences(texte, motif)`
    Elle renvoie le **nombre total d’occurrences** du motif dans le texte.

    ```python
    def nb_occurrences(texte, motif):
        """Renvoie le nombre de fois où motif apparaît dans texte"""
        pass

    assert nb_occurrences('bonjour monsieur gaboriot votre abonnement est fini', 'bo') == 3
    assert nb_occurrences(stendhal, 'Julien') == 1908
    assert nb_occurrences(stendhal, 'amour') == 225
    assert nb_occurrences(stendhal, 'informatique') == 0
    ```

    ??? success "✅ Solution"

        ```python
        def nb_occurrences(texte, motif):
            count = 0
            pos = texte.find(motif)

            while pos != -1:
                count += 1
                pos = texte.find(motif, pos + 1)

            return count
        
        assert nb_occurrences('bonjour monsieur gaboriot votre abonnement est fini', 'bo') == 3
        assert nb_occurrences(stendhal, 'Julien') == 1908
        assert nb_occurrences(stendhal, 'amour') == 225
        assert nb_occurrences(stendhal, 'informatique') == 0
        ```

---

???+ question "🧠 **Activité n°4 — Version récursive**"
    👉 Compléter la fonction `nb_occurrences(texte, motif)`.

    ```python
    def nb_occurrences(texte, motif):
        """renvoie le nombre de fois où motif apparaît dans texte """
        pass

    assert nb_occurrences('bonjour monsieur gaboriot votre abonnement est fini', 'bo') == 3
    assert nb_occurrences(stendhal, 'Julien') == 1908
    assert nb_occurrences(stendhal, 'amour') == 225
    assert nb_occurrences(stendhal, 'informatique') == 0
    ```

    ??? success "✅ Solution"

        ```python
        def nb_occurrences(texte, motif):
            compteur = 0
            i = texte.find(motif)

            while i != -1:
                compteur += 1
                i = texte.find(motif, i + 1)

            return compteur

        assert nb_occurrences('bonjour monsieur gaboriot votre abonnement est fini', 'bo') == 3
        assert nb_occurrences(stendhal, 'Julien') == 1908
        assert nb_occurrences(stendhal, 'amour') == 225
        assert nb_occurrences(stendhal, 'informatique') == 0
        ```

---





## <H2 STYLE="COLOR:BLUE;">🔎 <a name="_toc159537146"></a>**2. La recherche textuelle naïve**</H2>

---

### <H3 STYLE="COLOR:GREEN;">⚙️ <a name="_toc159537147"></a>**2.1. L’algorithme**</H3>

🎥 **Vidéo (6 premières minutes) : Recherche Boyer-Moore**
[https://ladigitale.dev/digiview/#/v/66c903de43b5c](https://ladigitale.dev/digiview/#/v/66c903de43b5c)

La **recherche naïve** (ou **force brute**) parcourt l’ensemble de la chaîne caractère après caractère.
À chaque position, on compare les lettres du motif avec celles du texte.

Le traitement est **simple**, **fiable**, mais **coûteux en temps**.

---

🖼️ **Illustrations**

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.001.png)

On compare chaque lettre du motif au texte.
Le **A** correspond, mais le **T** non → décalage.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.002.png)

Le **A** correspond mais le **C** non → décalage.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.003.png)

Le **C** ne correspond pas → décalage.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.004.png)

Le **A** et le **T** correspondent, mais le **G** non → décalage.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.005.png)

Le **A** ne correspond pas → décalage.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.006.png)

➡️ À chaque échec, on décale d’**un seul caractère** et on recommence.

---

### <H3 STYLE="COLOR:GREEN;">🧪 <a name="_toc159537148"></a>**2.2. Implémentation**</H3>

???+ question "🧠 **Activité n°5 — Implémenter la recherche naïve**"
    👉 Implémenter l’algorithme précédent en Python.

    ```python
    def recherche_naive(chaine, cle):
        long_txt = len(chaine)
        long_cle = len(cle)

        # Parcourir la chaîne de caractères
        pass
            # Tant que j est inférieur à la longueur de la clé et que
            # le caractère à la position i+j dans la chaîne est égal
            # au caractère à la position j dans la clé
            pass
            # Si j est égal à la longueur de la clé
            pass

        return -1


    texte = 'CAATGTCTGCACCAAGAC'
    motif = 'CAAG'
    assert recherche_naive(texte, motif) == 12
    assert recherche_naive(texte, 'BB') == -1
    ```

    ??? success "✅ Solution"

        ```python
        def recherche_naive(chaine, cle):
            long_txt = len(chaine)
            long_cle = len(cle)

            for i in range(long_txt - long_cle + 1):
                j = 0
                while j < long_cle and chaine[i + j] == cle[j]:
                    j += 1
                if j == long_cle:
                    return i

            return -1


        texte = 'CAATGTCTGCACCAAGAC'
        motif = 'CAAG'
        assert recherche_naive(texte, motif) == 12
        assert recherche_naive(texte, 'BB') == -1
        ```

---

### <H3 STYLE="COLOR:GREEN;">📈 <a name="_toc159537149"></a>**2.3. Complexité**</H3>

* Le texte contient **N** caractères
* Le motif contient **n** caractères
* Il y a **N − n + 1** positions possibles
* Chaque comparaison peut nécessiter jusqu’à **n** tests

➡️ **Complexité dans le pire des cas :**

$O(n^2)$

---

### <H3 STYLE="COLOR:GREEN;">⏱️ <a name="_toc159537150"></a>**2.4. Mesure du temps**</H3>

???+ question "🧠 **Activité n°6 — Comparer les temps d’exécution**"
    👉 Comparer la méthode intégrée `find()` et l’algorithme naïf.

    ```python
    from timeit import timeit

    def recherche_find(livre, texte):
        return livre.find(texte)

    def recherche_naif(livre, texte):
        return recherche_naive(livre, texte)

    livre = stendhal
    texte = 'Mme de Rênal fut fidèle à sa promesse'

    temps_find = timeit("recherche_find(livre, texte)", number=10, globals=globals())
    temps_naif = timeit("recherche_naif(livre, texte)", number=10, globals=globals())

    print("Temps en utilisant find :", temps_find)
    print("Temps en utilisant l'algorithme naïf :", temps_naif)
    ```

    ??? success "✅ Solution / Interprétation"

        * `find()` est **beaucoup plus rapide**

        * La recherche naïve devient **inefficace sur de grands textes**
        
        * ➜ **Besoin d’un algorithme optimisé**

---




## <H2 STYLE="COLOR:BLUE;"> <a name="_toc159537151"></a>**3. Application de l’algorithme de Boyer-Moore**</H2>
### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537152"></a>**3.1. Un cas concret**</H3>

L’algorithme : 

1\. On examine la chaîne, en partant du **bout de la clé**, et **en remontant les caractères de la clé un par un jusqu’à trouver une discordance**.

2\. Si la lettre de la chaîne examinée est identique à celle de la clé, **on remonte la clé**.

3\. Sinon on regarde si cette lettre existe dans la clé :

   1. Si elle n’existe pas : on peut faire un **saut maximal**.
   2. Sinon : on réalise un saut jusqu’à **sa position**.

**Animation**

<b>1<sup>er</sup> cas</b> :  la lettre n’est pas présente dans la clé.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.008.png)

On positionne la clé en début de la chaîne et on parcourt la chaîne à partir du dernier élément de la clé. E ne correspond pas au A et **il n’y a pas de E dans la clé.** On **décale la clé de la longueur de celle-ci** c’est-à-dire de 6 indices.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.009.png)

<b>2<sup>ème</sup> cas</b> : La lettre est présente dans la clé.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.014.png)

Le X est non concordant avec le A de la clé par contre **il est présent dans la clé à l’indice 1**.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.015.png)

On décale alors **de 4 indices**.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.016.png)

Et on continue.

<b>3<sup>ème</sup> cas</b> : une lettre présente dans la clé après quelques coïncidences.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.017.png)

A est en correspondance, G est en correspondance mais X n’est pas en correspondance mais **il se trouve dans la clé**.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.018.png)

On décale **de deux indices**.

![image](Aspose.Words.f7b0f1fb-05ce-44b0-ae07-c4f0af4f4ed2.019.png)

Et on continue.

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537153"></a>**3.2. Prétraitement du motif**</H3>

**Intérêt du prétraitement :** 

-\ l’algorithme connait les caractères qui se trouvent dans la clé.

-\ Avant de lancer l’algorithme il faut créer une table de saut pour chaque caractère de la clé.

  - Ecart minimal entre une lettre de la clé et la fin de la clé.
  - La dernière lettre est traitée à part : écart maximal si elle n’est pas présente ailleurs dans la clé.

Les sauts effectués lors du traitement permettent de réduire sa durée. Plus la clé est longue plus l’algorithme est efficace pour la trouver car les sauts sont en moyenne plus grands.

Pour construire la table de sauts pour TARTEMPION, l’algorithme teste d’abord le 10<sup>ème</sup> caractère de ce texte. Si c’est un N, il regarde si le 9<sup>ème</sup> caractère est un O, puis le 8<sup>ème</sup> ,…jusqu’au 1<sup>er</sup>.

Si le caractère lu est E il faut décaler de 5 positions.

On obtient ainsi la table de sauts suivante selon les lettres lues :

|A|R|T|E|M|P|I|O|Autre|
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|+8|+7|+6|+5|+4|+3|+2|+1|+10|

À chaque lecture d’une lettre, si la lettre correspond à la lettre recherchée, on compare les lettres précédentes pour vérifier s’il s’agit du motif cherché. Sinon, on utilise la table de sauts pour décaler la fenêtre de recherche.

**<H3 STYLE="COLOR:red;">Activité n° 7  : Algorithme pré-traitement :**</H3> Implémenter l’algorithme précédent en Python 
```python
def pre_traitement(mot):
    """Renvoie un dictionnaire avec pour clé la lettre et pour valeur le décalage"""
    decalages = {}
    n = len(mot)

    pass

assert pre_traitement("dab") == {'d': 2, 'a': 1}
assert pre_traitement("maman") == {'m': 2, 'a': 1}
```

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537154"></a>**3.3. L’algorithme**</H3>

La **première étape** est de réaliser le **pré-traitement c’est-à-dire la table de sauts**.

À chaque examen jusqu’à la fin de la chaîne (-longueur de la clé) : 

-\ Vérifier les **correspondances des caractères** en partant de la fin de la clé.

-\ Si correspondance, on remonte **la clé à l’envers**, lettre après lettre.

-\ Sinon, **on regarde dans la table de saut** si la lettre est présente :

  - Si la lettre est présente on fait le saut correspondant.
  - Si la lettre est non présente on fait le saut maximal.

**<H3 STYLE="COLOR:red;">Activité n° 8  : Algorithme boyer\_moore : Rajouter:**</H3>

Nous implémenterons une version qui retourne True si le mot est trouvé et False sinon
 
```python
def recherche_boyer(texte, mot):
    """Recherche un mot dans un texte avec l'algo de boyer-moore    """
    N = len(texte)
    n = len(mot)

    # création de notre dictionnaire de décalages
    decalages = pre_traitement(mot)

    # on commence à la fin du mot
    i = …
    
    while i < N:
        lettre = … # on récupère la lettre à la position i dans le texte
        if lettre == … # si la lettre est la dernière du mot

            # On vérifie que le mot est là avec un slice sur texte
            if …
                return True
        # on décale
        if lettre in …:
            i += …
        else:
            i += …

    return False


assert recherche_boyer('abracadabra', 'dab')
assert recherche_boyer('abracadabra', 'abra')
assert recherche_boyer('abracadabra', 'obra') is False
assert recherche_boyer('abracadabra', 'bara') is False
assert recherche_boyer('maman est là', 'maman')
assert recherche_boyer('bonjour maman', 'maman')
assert recherche_boyer('bonjour maman', 'papa') is False
```

### <H3 STYLE="COLOR:GREEN;"> <a name="_toc159537155"></a>**3.4. Comparaison des temps**</H3>

**<H3 STYLE="COLOR:red;">Activité n° 9  : Algorithme boyer\_moore : Rajouter:**</H3>
```python
temps_boyer = timeit("recherche_boyer(livre, texte)", number=10, globals=globals())
print("Temps en utilisant find : ",temps_naif)
print("Temps en utilisant l'algorithme Boyer-Moore : ",temps_boyer)
```
