## HC20T14 : mapMFilter : map-filter monadique

Implémenter une fonction monadique mapMFilter qui applique un mapping et un filtrage dans une monade.

---

### Code haskell

```haskell
-- mapMFilter : applique un mapping monadique puis filtre les résultats
mapMFilter :: Monad m => (a -> m (Maybe b)) -> [a] -> m [b]
mapMFilter f xs = fmap catMaybes (mapM f xs)
  where
    -- catMaybes : extrait les valeurs Just et ignore les Nothing
    catMaybes :: [Maybe b] -> [b]
    catMaybes = foldr (\x acc -> case x of
                                   Just v  -> v : acc
                                   Nothing -> acc) []
                                   
-- -------- Programme principal pour tester -----------
main :: IO ()
main = do
  let lst = [1..10]
  -- Exemple : on garde uniquement les nombres pairs et on double leur valeur
  result <- mapMFilter (\x -> return (if even x then Just (2*x) else Nothing)) lst
  putStrLn $ "Résultat : " ++ show result
```

---

### Explications

1. **Signature**

```haskell
mapMFilter :: Monad m => (a -> m (Maybe b)) -> [a] -> m [b]
```

* `a -> m (Maybe b)` : pour chaque élément, on peut :

  * retourner `Just b` → l’inclure dans le résultat,
  * retourner `Nothing` → l’exclure.
* La monade `m` permet de travailler avec `IO`, `Maybe`, `State`, etc.

2. **Implémentation**

* `mapM f xs` : applique le mapping monadique à chaque élément.
* `catMaybes` : supprime les `Nothing` pour ne garder que les valeurs `Just`.

3. **Exemple d’utilisation**

```haskell
mapMFilter (\x -> return (if even x then Just (2*x) else Nothing)) [1..10]
```

* Double les nombres pairs et ignore les impairs.
* Résultat attendu :

```
Résultat : [4,8,12,16,20]
```

---

💡 **Remarque :**
Cette approche est très générale et fonctionne avec **toutes les monades**, par exemple :

* `IO` : lire des entrées et filtrer certaines lignes.
* `Maybe` : appliquer une fonction qui peut échouer.
* `State` : appliquer un mapping tout en tenant compte d’un état.
