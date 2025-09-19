## HC20T2 : sequenceMaybe pour une liste de Maybe

Implémenter une fonction sequenceMaybe qui convertit une liste de valeurs Maybe en un Maybe de liste.

---

## Code haskell

```haskell
-- sequenceMaybe : [Maybe a] -> Maybe [a]
sequenceMaybe :: [Maybe a] -> Maybe [a]
sequenceMaybe [] = Just []
sequenceMaybe (x:xs) =
  case x of
    Nothing -> Nothing
    Just v  ->
      case sequenceMaybe xs of
        Nothing   -> Nothing
        Just rest -> Just (v : rest)

-- Exemple d’utilisation
main :: IO ()
main = do
  print $ sequenceMaybe [Just 1, Just 2, Just 3]
  print $ sequenceMaybe [Just 1, Nothing, Just 3]
```

🔹 **Résultat attendu :**

```
Just [1,2,3]
Nothing
```

---

### Explication

1. **Type**

   ```haskell
   sequenceMaybe :: [Maybe a] -> Maybe [a]
   ```

   * en entrée : une liste dont chaque élément est `Maybe a`
   * en sortie : un `Maybe [a]`

2. **Cas de base**

   * Si la liste est vide (`[]`), on retourne `Just []` :

     > une liste vide n’a aucun échec, donc le résultat est valide.

3. **Cas récursif**

   * On regarde la tête `x` :

     * si c’est `Nothing` → tout échoue → `Nothing`.
     * si c’est `Just v` → on applique récursivement `sequenceMaybe` sur la queue `xs`.

       * si ça renvoie `Nothing`, on garde `Nothing`.
       * sinon, on ajoute `v` au début de la liste retournée.

---

**Astuce** : Haskell fournit déjà cette logique via `sequence` ou `traverse` car `Maybe` est une monade !
On pourrait écrire directement :

```haskell
sequenceMaybe = sequence
```
