## HC5T7 : L’opérateur $

Réécrire la fonction suivante en utilisant l’opérateur $ :

result = sum (map (*2) (filter (>3) [1..10]))

Parfait 😄 En Haskell, l’opérateur **`$`** permet d’éviter les parenthèses en décalant l’application de fonctions vers la droite.

---

### Version originale

```haskell
result = sum (map (*2) (filter (>3) [1..10]))
```

---

### Réécriture avec `$`

```haskell
--La fonction reecrite avec $
result = sum $ map (*2) $ filter (>3) [1..10]

--La fonction principale 
main :: IO ()
main = print result
```

---

### Explications

1. **L’opérateur `$`**

   * Syntaxe : `f $ x` équivaut à `f x`.
   * Principal avantage : **évite les parenthèses imbriquées**.
   * Il a la **plus faible priorité**, donc tout ce qui est à droite est évalué avant d’être passé à la fonction de gauche.

2. **Équivalence**

   ```haskell
   sum $ map (*2) $ filter (>3) [1..10]
   ```

   * D’abord `filter (>3) [1..10]` → `[4,5,6,7,8,9,10]`
   * Ensuite `map (*2)` → `[8,10,12,14,16,18,20]`
   * Enfin `sum` → `98`

---

**Sortie :**

```
98
```
