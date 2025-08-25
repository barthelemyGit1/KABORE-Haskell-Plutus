## HC5T8 : Style point-free

Convertir la fonction suivante en style point-free :

addFive x = x + 5

---

### Version originale

```haskell
addFive :: Num a => a -> a
addFive x = x + 5
```

---

### Version point-free

```haskell

--La fonction avec le point-free
addFive :: Num a => a -> a
addFive = (+5)

--La fonction principale
main :: IO ()
main = do
    print $ addFive 10   -- 15
    print $ addFive 0    -- 5
    print $ addFive (-3) -- 2
```

---

### Explications

1. **`(+5)`**

   * C’est une fonction qui prend un argument et lui ajoute 5.
   * `(+)` est un opérateur infixe qui peut être utilisé comme fonction en entourant l’opération de parenthèses.

2. **Point-free**

   * On ne mentionne **pas `x`**.
   * `addFive` devient simplement l’application partielle de l’opérateur `+`.

---

**Sortie :**

```
15
5
2
```
