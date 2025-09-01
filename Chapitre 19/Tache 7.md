## HC19T7 : Fonction conditionalPrint avec when

Écrire une fonction conditionalPrint qui affiche un message uniquement si une condition est vraie, grâce à when.

---

### 1. Rappel : `when`

```haskell
when :: Monad m => Bool -> m () -> m ()
```

* Si la condition est `True`, exécute l’action `m ()`.
* Si la condition est `False`, ne fait rien (`return ()`).

---

### 2. Définition de la fonction

```haskell
import Control.Monad (when)

conditionalPrint :: Bool -> String -> IO ()
conditionalPrint condition message =
  when condition (putStrLn message)
```

### Explication

1. `conditionalPrint :: Bool -> String -> IO ()`

   * La fonction prend une **condition** (`Bool`) et un **message** (`String`) et retourne une action `IO` qui ne renvoie rien d’utile (`()`).

2. `when condition (putStrLn message)`

   * Si `condition` est `True` → exécute `putStrLn message`.
   * Sinon → ne fait rien.

---

### 3. Exemple d’utilisation

```haskell
main :: IO ()
main = do
  conditionalPrint True "Bonjour, condition vraie !"
  conditionalPrint False "Vous ne verrez jamais ce message"
```

**Résultat à l’écran :**

```
Bonjour, condition vraie !
```

* Le deuxième message n’apparaît pas car la condition est `False`.
