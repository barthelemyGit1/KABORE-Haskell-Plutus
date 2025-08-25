## HC7T7 : Utiliser Bounded et Enum

Créer une fonction nextColor qui prend une Color et retourne la couleur suivante dans l’ordre. Si c’est la dernière couleur, elle doit revenir à la première.

---

### Code Haskell

```haskell
-- Définition du type Color
data Color = Red | Green | Blue
    deriving (Show, Eq, Enum, Bounded)

-- Fonction pour obtenir la couleur suivante
nextColor :: Color -> Color
nextColor c
    | c == maxBound = minBound   -- Si c'est la dernière couleur, revenir à la première
    | otherwise     = succ c     -- Sinon passer à la couleur suivante

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ nextColor Red    -- Green
    print $ nextColor Green  -- Blue
    print $ nextColor Blue   -- Red
```

---

### Explications

1. **`Enum`**

   * Permet d’utiliser `succ` (successeur) et `pred` (prédécesseur) sur `Color`.
   * `succ Red = Green`, `succ Green = Blue`.

2. **`Bounded`**

   * Permet de connaître la **valeur minimale et maximale** : `minBound = Red`, `maxBound = Blue`.
   * Utile pour revenir au début si on dépasse la dernière couleur.

3. **Fonction `nextColor`**

   ```haskell
   nextColor c
       | c == maxBound = minBound
       | otherwise     = succ c
   ```

   * Si `c` est la dernière couleur → retourner la première.
   * Sinon → retourner la couleur suivante.

4. **Test**

   * On peut itérer à l’infini sur les couleurs en utilisant `nextColor`.

---

### Exemple de sortie

```
Green
Blue
Red
```

---

💡 Variante : on pourrait créer une **version circulaire pour n’importe quel type Enum et Bounded** :

```haskell
next :: (Eq a, Enum a, Bounded a) => a -> a
next x
    | x == maxBound = minBound
    | otherwise     = succ x
```
