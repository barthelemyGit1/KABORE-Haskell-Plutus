## HC6T6 : Existence d’un élément dans une liste

Implémente une fonction qui détermine si un élément donné existe dans une liste.

---

### Code Haskell

```haskell
-- Vérifie si un élément existe dans une liste
exists :: Eq a => a -> [a] -> Bool
exists _ [] = False                       -- Cas de base : liste vide -> élément absent
exists y (x:xs)
    | y == x    = True                    -- Si l’élément courant correspond -> trouvé
    | otherwise = exists y xs             -- Sinon on continue à chercher

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ exists 3 [1,2,3,4,5]      -- True
    print $ exists 6 [1,2,3,4,5]      -- False
    print $ exists 'a' "haskell"      -- True (car 'a' est dans la chaîne)
    print $ exists 'z' "haskell"      -- False
```

---

### Explications

1. **Cas de base**

   ```haskell
   exists _ [] = False
   ```

   * Si la liste est vide, l’élément n’existe pas.

2. **Cas récursif avec garde**

   ```haskell
   exists y (x:xs)
       | y == x    = True
       | otherwise = exists y xs
   ```

   * On compare `y` avec le premier élément `x`.
   * Si c’est égal → on retourne `True`.
   * Sinon → on continue la recherche dans le reste de la liste `xs`.

3. **Type**

   * `Eq a => a -> [a] -> Bool`
   * La fonction marche pour **tout type comparable (`Eq`)**.

---

### Exemple de sortie

```
True
False
True
False
```

---

💡 On pourrait aussi définir `exists` très simplement avec la fonction intégrée `elem` :

```haskell
exists = elem
```
