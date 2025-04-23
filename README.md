**Nom :** LEROY

**Groupe :** 3

**Année :** 2025

**IUT Le Havre - Cours GIT**

# TP 4 : Résolution de conflits et pull request

## Objectifs du TP 4

L’objectif de ce TP est double. D’une part, lorsque plusieurs personnes interagissent avec un référentiel Git, des conflits peuvent survenir, c’est-à-dire des problèmes d’intégration des changements produits par plusieurs utilisateurs. Le premier objectif de ce TP est :

- Apprendre à résoudre des conflits dans Git.
- Apprendre à utiliser l’option *pull request* pour collaborer sur un référentiel partagé.

---

## 1. Créer un conflit

### Étapes :

1. Créez un répertoire Git sur GitHub appelé `test-conflict` avec un fichier `README.md` contenant le texte suivant :

    ```markdown
    # test-conflict

    Normalement, dans le développement réel d'une application, des conflits se produiront spontanément. Cependant, pour notre formation, nous allons intentionnellement forcer un conflit dans git.

    Dans la plupart des cas, git est capable de mélanger les modifications que différents utilisateurs apportent à différents fichiers, mais si deux utilisateurs apportent des modifications au même fichier localement (surtout si la modification se trouve sur la même ligne), git ne pourra pas savoir quelle modification est la bonne. Produisons un tel conflit :

    Voici une ligne du README.md avec dex (deux) fotes de frape (fautes de frappe) à corriger.
    ```

2. **Athos** corrigera la première faute de frappe ("dex" en "deux") et **Porthos** corrigera la seconde faute ("fotes" en "fautes").
3. Chacun clone le répertoire et corrige sa faute de frappe localement.
4. N'oubliez pas de faire un `commit` des changements avant d’essayer de faire un `push` pour synchroniser les modifications avec le dépôt distant.
5. Empêchez Athos de faire un `git pull` avant que Porthos n'ait fait son `push`.

Lorsque Athos tente de faire un `push` après que Porthos a déjà poussé ses changements, un conflit sera généré.

---

## 2. Résoudre un conflit

### Étapes :

1. Athos utilise la commande `git diff` pour voir les différences :

    ```bash
    diff --cc README.md
    index 12d78ec,9c2e1f1..0000000
    --- a/README.md
    +++ b/README.md

    <<<<<<< HEAD
    - Voici une ligne du README.md avec deux fotes de frape (fautes de frappe) à corriger
    =======
    - Voici une ligne du README.md avec dex (deux) fautes de frappe à corriger
    >>>>>>> dcb10325482119cf4001d04049e285ea7fe2274a
    ```

2. Ouvrez `README.md` dans un éditeur de texte et résolvez le conflit. Modifiez la ligne en supprimant les marqueurs de conflit pour obtenir :

    ```markdown
    - Voici une ligne du README.md avec deux fautes de frappe à corriger
    ```

3. Une fois le conflit résolu, exécutez les commandes suivantes pour mettre à jour le référentiel local et distant :

    ```bash
    $ git status
    $ git add README.md
    $ git commit -m "Conflit README résolu"
    $ git push
    ```

---

## 3. Un exemple simple de pull request

Une pull request permet de proposer des modifications à un référentiel, même sans en être le propriétaire. Voici les étapes pour créer une pull request :

1. Faites un fork du répertoire `test-conflict`.
2. Créez une branche pour apporter vos modifications.
3. Faites un `commit` de vos modifications et poussez votre branche vers GitHub.
4. Ouvrez une pull request pour notifier le propriétaire du référentiel de vos modifications.

---

## Conclusion

Félicitations, on a résolu un conflit dans Git et appris à utiliser les *pull requests* pour collaborer sur un projet ! Ces concepts sont essentiels pour le travail d’équipe dans le développement logiciel.

