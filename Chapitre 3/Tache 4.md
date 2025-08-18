## HC3T4 - Tâche 4 : Calculer l’aire d’un triangle avec la formule de Héron

Définir une fonction triangleArea :: Float -> Float -> Float -> Float.

Utiliser let pour calculer le demi-périmètre s.

Appliquer la formule de Héron : sqrt(s * (s - a) * (s - b) * (s - c)).

Tester avec triangleArea 3 4 5 et triangleArea 7 8 9.

---

## ✅ Code Haskell

```haskell
-- Fonction triangleArea avec la formule de Héron
triangleArea :: Float -> Float -> Float -> Float
triangleArea a b c =
    let s = (a + b + c) / 2  -- demi-périmètre
    in sqrt (s * (s - a) * (s - b) * (s - c))

-- Fonction main pour tester
main :: IO ()
main = do
    print (triangleArea 3 4 5)  -- devrait donner 6.0
    print (triangleArea 7 8 9)  -- devrait donner environ 26.83
```

---

## 🧠 Explication détaillée

1. **Signature**

   ```haskell
   triangleArea :: Float -> Float -> Float -> Float
   ```

   La fonction prend **3 côtés** (`a`, `b`, `c`) et retourne un `Float` (l’aire).

2. **Calcul du demi-périmètre**

   ```haskell
   let s = (a + b + c) / 2
   ```

   Formule du demi-périmètre :

   $$
   s = \frac{a+b+c}{2}
   $$

3. **Formule de Héron**

   ```haskell
   sqrt (s * (s - a) * (s - b) * (s - c))
   ```

   Aire du triangle :

   $$
   A = \sqrt{s \cdot (s-a) \cdot (s-b) \cdot (s-c)}
   $$

4. **Tests**

   * `triangleArea 3 4 5`
     → $s = 6$,
     $A = \sqrt{6 \cdot 3 \cdot 2 \cdot 1} = \sqrt{36} = 6$. ✅

   * `triangleArea 7 8 9`
     → $s = 12$,
     $A = \sqrt{12 \cdot 5 \cdot 4 \cdot 3} = \sqrt{720} \approx 26.83$. ✅

---
