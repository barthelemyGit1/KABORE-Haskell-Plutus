## HC5T3 : Vérifier la présence de majuscules

Écrire une fonction utilisant any qui vérifie si une liste de mots contient au moins un mot commençant par une majuscule.

---

### Code Haskell

```haskell
import Data.Char (isUpper)

-- Fonction qui vérifie si un mot commence par une majuscule
startsWithUpper :: String -> Bool
startsWithUpper [] = False
startsWithUpper (c:_) = isUpper c

-- Fonction principale utilisant any
hasCapitalizedWord :: [String] -> Bool
hasCapitalizedWord words = any startsWithUpper words

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ hasCapitalizedWord ["hello", "world", "Haskell"]  -- True
    print $ hasCapitalizedWord ["hello", "world", "functional"] -- False
    print $ hasCapitalizedWord []                               -- False
```

---

### Explications

1. **`startsWithUpper`**

   * Vérifie si un mot commence par une majuscule.
   * `(c:_)` : pattern matching pour extraire le premier caractère `c`.
   * `isUpper c` : vrai si `c` est une lettre majuscule.
   * `[]` → mot vide → retourne `False`.

2. **`any`**

   ```haskell
   any startsWithUpper words
   ```

   * Parcourt la liste `words`.
   * Retourne `True` si **au moins un mot** satisfait `startsWithUpper`.

3. **Pureté**

   * Les deux fonctions sont **pures**, dépendant uniquement de leurs arguments.

---

### Exemple de sortie

```
True
False
False
```
