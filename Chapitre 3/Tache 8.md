## HC3T8 - Tâche avancée 8 : Calculer l’IMC et retourner la catégorie avec where

Définir bmiCategory :: Float -> Float -> String.

Utiliser where pour calculer l’IMC : bmi = poids / taille^2.

Utiliser des gardes pour classifier l’IMC :

<18.5 : « Insuffisance pondérale »

18.5 à 24.9 : « Normal »

25 à 29.9 : « Surpoids »

≥30 : « Obésité »

Tester avec bmiCategory 70 1.75 et bmiCategory 90 1.8.

---

## ✅ Code Haskell

```haskell
-- Fonction bmiCategory
bmiCategory :: Float -> Float -> String
bmiCategory poids taille
    | bmi < 18.5 = "Insuffisance pondérale"
    | bmi < 25   = "Normal"
    | bmi < 30   = "Surpoids"
    | otherwise  = "Obésité"
  where
    bmi = poids / (taille ^ 2)  -- calcul de l'IMC

-- Fonction principale pour tester
main :: IO ()
main = do
    print (bmiCategory 70 1.75)  -- "Normal"
    print (bmiCategory 90 1.8)   -- "Surpoids"
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   bmiCategory :: Float -> Float -> String
   ```

   * Prend le **poids** (kg) et la **taille** (m).
   * Retourne une `String` (catégorie de l’IMC).

2. **Calcul de l’IMC**

   ```haskell
   bmi = poids / (taille ^ 2)
   ```

   C’est fait dans la section `where`, donc on peut réutiliser `bmi` dans les gardes.

3. **Gardes (`|`)**

   * `< 18.5` → "Insuffisance pondérale"
   * `< 25`   → "Normal"
   * `< 30`   → "Surpoids"
   * `otherwise` → "Obésité"

4. **Tests**

   * `bmiCategory 70 1.75`
     $\text{IMC} = 70 / 1.75^2 ≈ 22.86$ → "Normal" ✅
   * `bmiCategory 90 1.8`
     $\text{IMC} = 90 / 1.8^2 ≈ 27.78$ → "Surpoids" ✅

---
