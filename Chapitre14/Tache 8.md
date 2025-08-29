## HC14T8 : Fonction de comptage de fréquence de caractères 

Implémenter une fonction counts qui retourne une liste de tuples représentant la fréquence des caractères dans une chaîne.

---

## 1️⃣ Code Haskell complet

```haskell
module CharCounts where

import Data.List (group, sort)

-- | Fonction qui retourne la fréquence des caractères
counts :: String -> [(Char, Int)]
counts str =
    map (\grp -> (head grp, length grp)) $ group $ sort str
```

### Explications :

1. **`sort str`**

   * Trie tous les caractères de la chaîne.
   * Exemple : `"hello"` → `"ehllo"`.

2. **`group`**

   * Regroupe les caractères identiques consécutifs dans des sous-listes.
   * Exemple : `"ehllo"` → `["e","h","ll","o"]`.

3. **`map (\grp -> (head grp, length grp))`**

   * Transforme chaque groupe en un tuple `(caractère, nombre d’occurrences)`.
   * Exemple : `["l","l"]` → `('l', 2)`.

---

## 2️⃣ Exemple d’utilisation

```haskell
main :: IO ()
main = do
    let text = "hello world"
    print $ counts text
```

### Résultat attendu :

```
[(' ',1),('d',1),('e',1),('h',1),('l',3),('o',2),('r',1),('w',1)]
```

* Chaque tuple représente `(caractère, fréquence)`.
* Les caractères sont triés.

---

## 3️⃣ Notes

* Si tu veux **ignorer la casse**, tu peux utiliser `import Data.Char (toLower)` et transformer la chaîne avec `map toLower str`.
* Pour **ignorer les espaces ou autres caractères**, tu peux filtrer la chaîne avant le comptage :

```haskell
counts $ filter (/= ' ') $ map toLower str
```
