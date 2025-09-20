## HC20T12 : Lecture de fichier avec la monade IO

Utiliser la monade IO pour lire un fichier et afficher son contenu ligne par ligne.

Voici un exemple complet en **Haskell** pour lire un fichier et afficher son contenu ligne par ligne en utilisant la **monade `IO`**.

---

## Code haskell

```haskell
-- HC20T12 : Lecture de fichier avec la monade IO

main :: IO ()
main = do
  putStrLn "Entrez le nom du fichier à lire :"
  filename <- getLine                -- Lire le nom du fichier depuis l'utilisateur
  content <- readFile filename       -- Lire tout le contenu du fichier
  let linesOfFile = lines content   -- Séparer le contenu en lignes
  putStrLn "\nContenu du fichier :"
  mapM_ putStrLn linesOfFile         -- Afficher chaque ligne
```

---

### Explications

1. **`getLine`**

   * Lit une ligne de l’entrée standard (ici le nom du fichier).

2. **`readFile`**

   * Lit le contenu du fichier donné en paramètre.
   * Retourne une `String` complète.

3. **`lines`**

   * Sépare la `String` en une liste de chaînes (`[String]`) correspondant aux lignes.

4. **`mapM_ putStrLn`**

   * Parcourt la liste de lignes et les affiche une par une.
   * `mapM_` est utilisé pour exécuter une action `IO` sur chaque élément d’une liste sans accumuler de résultats.

---

### Exemple d’exécution

Supposons que le fichier `test.txt` contient :

```
Bonjour
Comment ça va ?
Haskell est fun !
```

Exécution :

```
Entrez le nom du fichier à lire :
test.txt

Contenu du fichier :
Bonjour
Comment ça va ?
Haskell est fun !
```

---

💡 **Remarque :**

* Tout est dans la **monade `IO`**, donc les actions d’entrée/sortie se font de manière séquentielle.
* Si le fichier n’existe pas, Haskell lèvera une exception.
  On peut utiliser `try` ou `catch` pour gérer les erreurs proprement si nécessaire.

---
