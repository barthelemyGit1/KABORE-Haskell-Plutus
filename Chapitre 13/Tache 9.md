## HC13T9 : Renommer un espace de noms de module

Créer une fonction qui démontre le renommage d’un espace de noms de module et utilise des fonctions des deux modules renommés.

---

## Code haskell

### 1️⃣ Modules existants

#### `MyMath.hs`

```haskell
module MyMath (sum, multiply) where

sum :: Int -> Int -> Int
sum x y = x + y

multiply :: Int -> Int -> Int
multiply x y = x * y
```

#### `MyList.hs`

```haskell
module MyList (sum, reverseList) where

sum :: [Int] -> Int
sum xs = foldr (+) 0 xs

reverseList :: [Int] -> [Int]
reverseList = reverse
```

---

### 2️⃣ Programme principal `Main.hs` avec renommage

```haskell
-- On renomme les modules importés pour éviter les conflits de noms
import qualified MyMath as Math
import qualified MyList as List

main :: IO ()
main = do
    let a = 7
        b = 3
        nums = [1,2,3,4]

    -- Utilisation de MyMath.sum via le nouvel alias Math
    let totalMath = Math.sum a b
    putStrLn $ "Math.sum " ++ show a ++ " + " ++ show b ++ " = " ++ show totalMath

    -- Utilisation de MyList.sum via le nouvel alias List
    let totalList = List.sum nums
    putStrLn $ "List.sum " ++ show nums ++ " = " ++ show totalList

    -- Utilisation d'une autre fonction des deux modules
    putStrLn $ "Math.multiply " ++ show a ++ " * " ++ show b ++ " = " ++ show (Math.multiply a b)
    putStrLn $ "List.reverseList " ++ show nums ++ " = " ++ show (List.reverseList nums)
```

---

### 3️⃣ Explications

1. **Renommage avec `as`**

   ```haskell
   import qualified MyMath as Math
   import qualified MyList as List
   ```

   * On donne un **alias** (`Math` et `List`) aux modules importés.
   * Cela permet d’utiliser leurs fonctions avec ces préfixes et de résoudre les conflits de noms.

2. **Appel des fonctions**

   * `Math.sum` → somme de deux entiers
   * `List.sum` → somme d’une liste d’entiers
   * Les deux peuvent coexister grâce aux alias.

3. **Avantage**

   * Clarté dans le code et pas de conflit de noms même si plusieurs modules exportent la même fonction.

---

### 4️⃣ Résultat attendu

```
Math.sum 7 + 3 = 10
List.sum [1,2,3,4] = 10
Math.multiply 7 * 3 = 21
List.reverseList [1,2,3,4] = [4,3,2,1]
```
