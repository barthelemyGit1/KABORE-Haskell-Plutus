## HC20T13 : fibonacciMemo avec la monade State

Créer une fonction fibonacciMemo utilisant la monade State pour mémoïser le calcul des Fibonacci.

---

### Code complet

```haskell
import Control.Monad.State
import qualified Data.Map as Map

-- Type alias pour l'état de mémoïsation
type Memo = Map.Map Int Integer

-- fibonacciMemo : calcule le n-ième Fibonacci avec mémoïsation
fibonacciMemo :: Int -> State Memo Integer
fibonacciMemo 0 = return 0
fibonacciMemo 1 = return 1
fibonacciMemo n = do
  memo <- get
  case Map.lookup n memo of
    Just value -> return value           -- Valeur déjà calculée
    Nothing -> do
      f1 <- fibonacciMemo (n - 1)
      f2 <- fibonacciMemo (n - 2)
      let result = f1 + f2
      modify (Map.insert n result)       -- Stocker le résultat dans l'état
      return result

-- Fonction pour exécuter le calcul avec un état initial vide
runFib :: Int -> Integer
runFib n = evalState (fibonacciMemo n) Map.empty

-- ----------- Programme principal -----------
main :: IO ()
main = do
  putStrLn "Entrez n pour calculer Fibonacci(n) :"
  input <- getLine
  let n = read input :: Int
      result = runFib n
  putStrLn $ "Fibonacci(" ++ show n ++ ") = " ++ show result
```

---

### Explications

1. **Monade `State`**

   * On utilise `State Memo Integer` pour transporter une table de mémoïsation (`Map Int Integer`) pendant le calcul.
   * Cela évite de recalculer plusieurs fois les mêmes Fibonacci.

2. **Mémoïsation**

   * `get` : récupère l’état actuel (`Map`).
   * `Map.lookup n memo` : vérifie si `Fibonacci(n)` a déjà été calculé.
   * `modify (Map.insert n result)` : stocke le résultat dans l’état après calcul.

3. **Récursivité**

   * `fibonacciMemo (n-1)` et `fibonacciMemo (n-2)` sont appelés récursivement.
   * La monade `State` gère automatiquement la propagation du dictionnaire de mémoïsation.

4. **Exécution**

   * `evalState (fibonacciMemo n) Map.empty` : démarre avec une table vide.

---

### Exemple d’exécution

```
Entrez n pour calculer Fibonacci(n) :
10
Fibonacci(10) = 55
```

💡 **Remarque :**
Cette approche permet de calculer efficacement des valeurs élevées de Fibonacci sans explosion combinatoire, grâce à la **mémoïsation avec `State`**.
