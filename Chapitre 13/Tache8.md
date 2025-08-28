## HC13T8 : Importations qualifiées pour les conflits de noms

Montrer comment gérer les conflits de noms entre deux modules importés en utilisant les importations qualifiées.

---

## Code haskell

### 1️⃣ Module `MyMath.hs`

```haskell
module MyMath (sum, multiply) where

-- Addition de deux entiers
sum :: Int -> Int -> Int
sum x y = x + y

-- Multiplication de deux entiers
multiply :: Int -> Int -> Int
multiply x y = x * y
```

---

### 2️⃣ Module `MyList.hs`

```haskell
module MyList (sum, reverseList) where

-- Somme d'une liste d'entiers
sum :: [Int] -> Int
sum xs = foldr (+) 0 xs

-- Inverse une liste
reverseList :: [Int] -> [Int]
reverseList = reverse
```

---

### 3️⃣ Programme principal `Main.hs`

```haskell
import qualified MyMath as M
import qualified MyList as L

main :: IO ()
main = do
    let a = 10
        b = 20
        lst = [1,2,3,4,5]

    -- Utilisation de MyMath.sum
    let totalMath = M.sum a b
    putStrLn $ "MyMath.sum " ++ show a ++ " + " ++ show b ++ " = " ++ show totalMath

    -- Utilisation de MyList.sum
    let totalList = L.sum lst
    putStrLn $ "MyList.sum " ++ show lst ++ " = " ++ show totalList

    -- Utilisation d'une autre fonction
    putStrLn $ "MyList.reverseList " ++ show lst ++ " = " ++ show (L.reverseList lst)
```

---

### 4️⃣ Explications

1. **Modules qualifiés**

   * `import qualified MyMath as M` → les fonctions du module MyMath sont préfixées par `M.`
   * `import qualified MyList as L` → les fonctions du module MyList sont préfixées par `L.`

2. **Résolution du conflit**

   * Les deux modules exportent `sum`.
   * Grâce aux préfixes, on peut utiliser **les deux fonctions dans le même fichier** sans ambiguïté.

3. **Résultat attendu** :

```
MyMath.sum 10 + 20 = 30
MyList.sum [1,2,3,4,5] = 15
MyList.reverseList [1,2,3,4,5] = [5,4,3,2,1]
```
