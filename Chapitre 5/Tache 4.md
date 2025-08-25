## HC5T4 : Utiliser les fonctions lambda 

Réécrire la fonction suivante en utilisant une fonction lambda : biggerThan10 x = x > 10

---

### Version originale

```haskell
biggerThan10 :: Int -> Bool
biggerThan10 x = x > 10
```

---

### Version avec **lambda**

```haskell
biggerThan10 :: Int -> Bool
biggerThan10 = \x -> x > 10

-- Fonction principale
main :: IO ()
main = do
    print $ biggerThan10 5    -- False
    print $ biggerThan10 15   -- True
    print $ filter biggerThan10 [5,12,3,20] -- [12,20]
```

---

### Explications

1. **`\x -> x > 10`**

   * `\x` indique que c’est une **fonction prenant un argument `x`**.
   * `x > 10` est l’expression qui sera retournée.
   * Cela remplace la définition classique `biggerThan10 x = x > 10`.

2. **Avantage**

   * La fonction devient **point-free** : pas besoin de mentionner le nom de l’argument dans la définition principale.
   * Utile pour passer directement à des fonctions comme `filter` ou `map`.
--- 

**Sortie :**

```
False
True
[12,20]
```
