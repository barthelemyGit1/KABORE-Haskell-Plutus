## HC20T4 : countChars avec la monade State

Implémenter une fonction countChars qui compte les occurrences d’un caractère dans une chaîne à l’aide de la monade State.

---

### Code haskell

```haskell
import Control.Monad.State
import Control.Monad (when)

-- | Compte les occurrences d'un caractère dans une chaîne en utilisant State
countChars :: Char -> String -> Int
countChars c s = execState (mapM_ step s) 0
  where
    step :: Char -> State Int ()     -- <-- annotation nécessaire
    step x = when (x == c) $ modify (+1)

-- Exemple d'utilisation
main :: IO ()
main = do
  let txt = "hello world"
  putStrLn $ "Texte : " ++ txt
  putStrLn $ "Nombre de 'l' : " ++ show (countChars 'l' txt)
  putStrLn $ "Nombre de 'o' : " ++ show (countChars 'o' txt)

```

---

## Explication

* **`State Int`** :

  * Le *state* contient un entier = le compteur.
  * `execState` exécute le calcul et retourne **seulement** l’état final (le nombre).

* `mapM_ step s` : applique l’action `step` à chaque caractère de la chaîne.

* `step` :

  ```haskell
  when (x == c) $ modify (+1)
  ```

  * Si le caractère courant `x` est celui qu’on cherche, on incrémente le compteur avec `modify`.

---

### Exemple d’exécution

```text
Texte : hello world
Nombre de 'l' : 3
Nombre de 'o' : 2
```

---

💡 **À retenir**
La monade `State` est parfaite pour manipuler un état mutable de façon pure :
ici, on garde un compteur sans avoir à passer explicitement la valeur courante entre les appels.
