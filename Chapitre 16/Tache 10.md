## HC16T10: Fréquence des caractères d'une chaîne

Définir une fonction qui compte la fréquence de chaque caractère dans une chaîne.

---

## ✅ Code Haskell

```haskell
module Main where

import Data.List (group, sort)

-- Fonction qui compte la fréquence de chaque caractère
frequenceChars :: String -> [(Char, Int)]
frequenceChars str =
    map (\grp -> (head grp, length grp)) $ group $ sort str

main :: IO ()
main = do
    let texte = "haskell est fun"
    putStrLn $ "Texte : " ++ texte
    putStrLn $ "Fréquence des caractères : " ++ show (frequenceChars texte)
```

---

## 📝 Explication

1. **Importation**

   ```haskell
   import Data.List (group, sort)
   ```

   * `sort` : trie la chaîne pour que les mêmes caractères soient contigus.
   * `group` : regroupe les éléments identiques consécutifs en sous-listes.

2. **Fonction `frequenceChars`**

   ```haskell
   frequenceChars str =
       map (\grp -> (head grp, length grp)) $ group $ sort str
   ```

   * `sort str` : trie la chaîne.
   * `group` : transforme `"aabbc"` en `[["a","a"],["b","b"],["c"]]`.
   * `map (\grp -> (head grp, length grp))` : convertit chaque sous-liste en tuple `(caractère, nombre d'occurrences)`.

3. **Exemple d’exécution**

   ```
   Texte : haskell est fun
   Fréquence des caractères : [(' ',2),('a',1),('e',2),('f',1),('h',1),('k',1),('l',2),('n',1),('s',2),('t',1),('u',1)]
   ```
