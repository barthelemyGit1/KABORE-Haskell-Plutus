## HC3T3 - Tâche 3 : Convertir une couleur RGB en chaîne hexadécimale avec let

Définir une fonction rgbToHex :: (Int, Int, Int) -> String.

Utiliser des let pour formater chaque composant couleur en une chaîne hexadécimale à deux caractères.

Concaténer les trois valeurs hexadécimales en une seule chaîne.

Tester la fonction avec rgbToHex (255, 0, 127) et rgbToHex (0, 255, 64).

---

## ✅ Code Haskell

```haskell
import Text.Printf (printf)

-- Fonction rgbToHex
rgbToHex :: (Int, Int, Int) -> String
rgbToHex (r, g, b) =
    let rHex = printf "%02X" r
        gHex = printf "%02X" g
        bHex = printf "%02X" b
    in "#" ++ rHex ++ gHex ++ bHex

-- Fonction main pour tester
main :: IO ()
main = do
    print (rgbToHex (255, 0, 127))  -- "#FF007F"
    print (rgbToHex (0, 255, 64))   -- "#00FF40"
```

---

## 🧠 Explication

1. **Importation**

   ```haskell
   import Text.Printf (printf)
   ```

   On importe `printf`, une fonction pratique pour formater les nombres comme en C.

2. **Signature**

   ```haskell
   rgbToHex :: (Int, Int, Int) -> String
   ```

   * La fonction prend un triplet d’entiers `(r, g, b)`.
   * Elle retourne une chaîne (`String`).

3. **Conversion en hexadécimal**

   ```haskell
   let rHex = printf "%02X" r
       gHex = printf "%02X" g
       bHex = printf "%02X" b
   ```

   * `%02X` → format hexadécimal avec **2 chiffres minimum**, en majuscules, et avec `0` devant si besoin.
   * Exemple :

     * `printf "%02X" 255` → `"FF"`
     * `printf "%02X" 0` → `"00"`
     * `printf "%02X" 127` → `"7F"`

4. **Concaténation**

   ```haskell
   in "#" ++ rHex ++ gHex ++ bHex
   ```

   On ajoute `#` puis on colle les 3 chaînes hexadécimales ensemble.

5. **Exécution**

   ```haskell
   print (rgbToHex (255, 0, 127))  -- "#FF007F"
   print (rgbToHex (0, 255, 64))   -- "#00FF40"
   ```

---

## ▶️ Résultat attendu

```
"#FF007F"
"#00FF40"
```

---
