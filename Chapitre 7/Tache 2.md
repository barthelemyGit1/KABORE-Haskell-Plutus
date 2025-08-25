## HC7T2 : Implémenter une instance Ord pour un type personnalisé

En utilisant le type Color de HC7T1, implémenter la classe de type Ord pour que Red < Green < Blue.

```
Red < Green < Blue
```

---

### Code Haskell

```haskell
-- Définition du type Color
data Color = Red | Green | Blue
    deriving (Eq, Show)   -- On dérive Eq et Show pour faciliter les comparaisons et l'affichage

-- Implémentation de l'instance Ord
instance Ord Color where
    compare Red Red     = EQ
    compare Green Green = EQ
    compare Blue Blue   = EQ
    compare Red Green   = LT
    compare Red Blue    = LT
    compare Green Blue  = LT
    compare Green Red   = GT
    compare Blue Red    = GT
    compare Blue Green  = GT

-- Fonction principale pour tester
main :: IO ()
main = do
    print (Red < Green)     -- True
    print (Green < Blue)    -- True
    print (Blue > Red)      -- True
    print (compare Red Blue) -- LT
    print (compare Green Red) -- GT
```

---

### Explications

1. **Type `Color`**

   ```haskell
   data Color = Red | Green | Blue
   ```

   * Trois constructeurs représentant les couleurs.

2. **Classe `Ord`**

   ```haskell
   instance Ord Color where ...
   ```

   * On définit **comment comparer deux couleurs**.
   * `compare` retourne `LT`, `EQ` ou `GT`.

3. **Ordre choisi**

   * `Red < Green < Blue`.
   * Donc :

     * `Red` est toujours plus petit que `Green` et `Blue`.
     * `Green` est plus grand que `Red` mais plus petit que `Blue`.
     * `Blue` est le plus grand.

4. **Tests**

   * On peut utiliser `<`, `>`, `<=`, `>=` et `compare`.

---

### Exemple de sortie

```
True
True
True
LT
GT
---
