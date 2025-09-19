## HC20T6 : doubleMonad combinant Maybe et List

Implémenter une fonction doubleMonad qui combine deux Monads : Maybe et List.

---

## Code haskell

```haskell
import Control.Monad
import Control.Monad.Trans.Maybe

-- Notre fonction combinée
doubleMonad :: [Maybe Int] -> MaybeT [] Int
doubleMonad xs = MaybeT xs

test :: MaybeT [] Int
test = do
    x <- doubleMonad [Just 1, Nothing, Just 3]
    y <- doubleMonad [Just 10, Just 20]
    return (x + y)

main :: IO ()
main = print (runMaybeT test)
```

**Résultat :**

```haskell
[Just 11,Just 21,Nothing,Just 13,Just 23,Nothing]
```

---

### 🧾 Explication

1. `doubleMonad` encapsule une liste de `Maybe` dans `MaybeT []`.
2. Dans le `do`, on peut :

   * propager l’échec (`Nothing`) automatiquement,
   * explorer plusieurs choix possibles (venant de `[]`).
3. Le résultat final est une **liste de résultats potentiellement échoués**.

---

En résumé, `doubleMonad` combine bien les deux effets :

* **l’échec possible** (via `Maybe`)
* **la non-détermination** (via `[]`)
