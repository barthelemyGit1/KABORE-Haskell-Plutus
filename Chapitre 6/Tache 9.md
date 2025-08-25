## HC6T9 : Implémentation de map

Implémente une fonction qui applique une fonction à chaque élément d’une liste (comme map).

---

### Code Haskell

```haskell
-- Implémentation personnalisée de map
myMap :: (a -> b) -> [a] -> [b]
myMap _ []     = []                 -- Cas de base : liste vide
myMap f (x:xs) = f x : myMap f xs   -- Cas récursif : appliquer f au premier élément, puis au reste

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ myMap (+1) [1,2,3,4]       -- [2,3,4,5]
    print $ myMap (*2) [1,2,3,4]       -- [2,4,6,8]
    print $ myMap (++ "!") ["Hi","Yo"] -- ["Hi!","Yo!"]
    print $ myMap length ["a","ab","abc"] -- [1,2,3]
```

---

### Explications

1. **Type**

   ```haskell
   myMap :: (a -> b) -> [a] -> [b]
   ```

   * Prend une fonction `f` qui transforme un élément de type `a` en `b`.
   * Prend une liste `[a]`.
   * Retourne une nouvelle liste `[b]`.

2. **Cas de base**

   ```haskell
   myMap _ [] = []
   ```

   * Une liste vide appliquée à n’importe quelle fonction donne une liste vide.

3. **Cas récursif**

   ```haskell
   myMap f (x:xs) = f x : myMap f xs
   ```

   * On applique `f` au premier élément `x`.
   * On appelle récursivement `myMap` sur le reste `xs`.
   * On construit une nouvelle liste avec `:`.

---

### Exemple de sortie

```
[2,3,4,5]
[2,4,6,8]
["Hi!","Yo!"]
[1,2,3]
```
