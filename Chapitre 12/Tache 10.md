## HC12T10 : Module d’opérations mathématiques

Créer un programme Haskell qui définit un module pour les opérations mathématiques et démontre son utilisation dans la fonction main.

---

### Code haskell

### 1️⃣ Module `MathOps.hs`

Crée un fichier `MathOps.hs` :

```haskell
module MathOps (
    add,
    subtract',
    multiply,
    divide
) where

-- Addition
add :: Num a => a -> a -> a
add x y = x + y

-- Soustraction
subtract' :: Num a => a -> a -> a
subtract' x y = x - y

-- Multiplication
multiply :: Num a => a -> a -> a
multiply x y = x * y

-- Division (floating point)
divide :: Fractional a => a -> a -> a
divide x y = x / y
```

---

### 2️⃣ Programme principal `Main.hs`

Crée un fichier `Main.hs` dans le même dossier :

```haskell
import MathOps

main :: IO ()
main = do
    putStrLn "Exemple d'utilisation du module MathOps :"

    let a = 10
    let b = 5

    putStrLn $ "Addition : " ++ show (add a b)
    putStrLn $ "Soustraction : " ++ show (subtract' a b)
    putStrLn $ "Multiplication : " ++ show (multiply a b)
    putStrLn $ "Division : " ++ show (divide (fromIntegral a) (fromIntegral b))
```

---

### 3️⃣ Explications

1. **Module `MathOps`** :

   * Contient les fonctions mathématiques de base.
   * L’export liste les fonctions accessibles depuis l’extérieur (`add`, `subtract'`, etc.).

2. **Main** :

   * Importe le module avec `import MathOps`.
   * Utilise les fonctions définies dans le module.

3. **Compilation et exécution** :

```bash
ghc Main.hs
./Main
```

---
