## HC3T6 - Tâche avancée 6 : Vérifier une année bissextile avec if-then-else

Définir isLeapYear :: Int -> Bool.

Utiliser if-then-else pour vérifier :

Divisible par 400 : True

Divisible par 100 mais pas par 400 : False

Divisible par 4 : True

Sinon : False

Tester avec isLeapYear 2000, isLeapYear 1900 et isLeapYear 2024.

---

## ✅ Code Haskell

```haskell
-- Fonction isLeapYear
isLeapYear :: Int -> Bool
isLeapYear year =
    if year `mod` 400 == 0 then True
    else if year `mod` 100 == 0 then False
    else if year `mod` 4 == 0 then True
    else False

-- Fonction principale pour tester
main :: IO ()
main = do
    print (isLeapYear 2000)  -- True (divisible par 400)
    print (isLeapYear 1900)  -- False (divisible par 100 mais pas par 400)
    print (isLeapYear 2024)  -- True (divisible par 4)
    print (isLeapYear 2023)  -- False
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   isLeapYear :: Int -> Bool
   ```

   * La fonction prend une année (`Int`).
   * Elle retourne `True` si l’année est bissextile, `False` sinon.

2. **Règles**

   * **Si divisible par 400 → bissextile (`True`)**
     Ex : 2000
   * **Si divisible par 100 mais pas par 400 → pas bissextile (`False`)**
     Ex : 1900
   * **Si divisible par 4 → bissextile (`True`)**
     Ex : 2024
   * **Sinon → pas bissextile (`False`)**
     Ex : 2023

3. **Opérateur modulo**

   * `year \`mod\` 400 == 0`→ teste si`year\` est divisible par 400.
   * Même logique pour `100` et `4`.

---

## ▶️ Résultat attendu

```
True
False
True
False
```
