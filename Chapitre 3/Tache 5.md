## HC3T5 - Tâche 5 : Déterminer le type d’un triangle avec des gardes

Définir une fonction triangleType :: Float -> Float -> Float -> String.

Utiliser des gardes pour classifier le triangle :

Tous les côtés égaux : « Équilatéral »

Deux côtés égaux : « Isocèle »

Aucun côté égal : « Scalène »

Tester avec triangleType 3 3 3, triangleType 5 5 8 et triangleType 6 7 8.

---

## ✅ Code Haskell

```haskell
-- Fonction triangleType
triangleType :: Float -> Float -> Float -> String
triangleType a b c
    | a == b && b == c          = "Équilatéral"
    | a == b || b == c || a == c = "Isocèle"
    | otherwise                  = "Scalène"

-- Fonction principale pour tester
main :: IO ()
main = do
    print (triangleType 3 3 3)  -- "Équilatéral"
    print (triangleType 5 5 8)  -- "Isocèle"
    print (triangleType 6 7 8)  -- "Scalène"
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   triangleType :: Float -> Float -> Float -> String
   ```

   * La fonction prend 3 côtés (`Float`) et retourne une chaîne (`String`).

2. **Gardes**

   * `| a == b && b == c` → si les 3 côtés sont égaux → **Équilatéral**.
   * `| a == b || b == c || a == c` → si au moins 2 côtés sont égaux → **Isocèle**.
   * `| otherwise` → sinon → **Scalène** (tous les côtés différents).

3. **Tests**

   * `triangleType 3 3 3` → Équilatéral ✅
   * `triangleType 5 5 8` → Isocèle ✅
   * `triangleType 6 7 8` → Scalène ✅

---

## ▶️ Résultat attendu

```
"Équilatéral"
"Isocèle"
"Scalène"
```

---
