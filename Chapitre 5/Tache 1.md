## HC5T1 : Utiliser applyTwice

Définir une fonction qui prend une fonction et un entier, puis applique la fonction trois fois à l’entier.

---

### Code Haskell

```haskell
-- Fonction qui applique une fonction deux fois
applyTwice :: (a -> a) -> a -> a
applyTwice f x = f (f x)

-- Fonction qui applique une fonction trois fois
applyThrice :: (a -> a) -> a -> a
applyThrice f x = f (f (f x))

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ applyThrice (+2) 5       -- ((5+2)+2)+2 = 11
    print $ applyThrice (*3) 2       -- ((2*3)*3)*3 = 54
    print $ applyThrice (\x -> x^2) 2 -- (((2^2)^2)^2) = 16
```

---

### Explications

1. **`applyTwice`**

   ```haskell
   applyTwice f x = f (f x)
   ```

   * Applique la fonction `f` **deux fois** sur l’argument `x`.
   * Exemple : `applyTwice (+1) 5` → `7`.

2. **`applyThrice`**

   ```haskell
   applyThrice f x = f (f (f x))
   ```

   * Même principe, mais appliqué **trois fois**.
   * Exemple : `applyThrice (+2) 5` → `11`.

3. **Avantages**

   * Fonction **générique** : fonctionne pour tout type `a` compatible avec la fonction `f`.
   * Illustrable facilement avec des fonctions comme `+`, `*` ou des lambdas.

---

### Exemple de sortie

```
11
54
16
```
