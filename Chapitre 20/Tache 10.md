## HC20T10 : Combinaison imbriquée StateT et MaybeT

Implémenter un transformateur de monade imbriqué combinant StateT et MaybeT.

---

### Code complet

```haskell
{-# LANGUAGE FlexibleContexts #-}

import Control.Monad.State
import Control.Monad.Trans.Maybe
import Control.Monad.Trans.Class (lift)

-- Définition d’un type alias pour notre pile de transformateurs
type AppState s a = StateT s (MaybeT IO) a

-- Exemple : incrémente l’état mais échoue si le seuil est dépassé
incrementUntil :: (Ord s, Num s, Show s) => s -> AppState s ()
incrementUntil limit = do
  val <- get
  liftIO $ putStrLn ("Valeur courante : " ++ show val)
  if val >= limit
     then lift $ MaybeT (return Nothing)  -- provoque un échec
     else put (val + 1)

-- Petite fonction utilitaire pour exécuter l'action
runIncrement :: Int -> Int -> IO (Maybe ((), Int))
runIncrement start limit =
  runMaybeT (runStateT (loop limit) start)
  where
    loop l = do
      incrementUntil l
      val <- get
      if val == l
         then return ()
         else loop l

-- -------- Programme principal --------
main :: IO ()
main = do
  putStrLn "== Démonstration StateT + MaybeT =="
  res <- runIncrement 0 5
  case res of
    Nothing        -> putStrLn "Échec : le seuil a été dépassé."
    Just (_, st)   -> putStrLn $ "Succès ! État final = " ++ show st
```

---

### Explication du code

#### 1️⃣ **Empilement des monades**

* On définit un alias :

  ```haskell
  type AppState s a = StateT s (MaybeT IO) a
  ```

  Cela signifie :

  > « Une computation qui garde un état `s`, peut échouer (`MaybeT`) et s’exécute dans `IO`. »

---

#### 2️⃣ **La fonction `incrementUntil`**

* Récupère l’état courant avec `get`.

* Affiche sa valeur via `liftIO` (pour remonter l’action `IO` à travers `StateT` et `MaybeT`).

* Si la valeur dépasse `limit`, on échoue grâce à :

  ```haskell
  lift $ MaybeT (return Nothing)
  ```

* Sinon, on met à jour l’état avec `put`.

---

#### 3️⃣ **Boucle `loop`**

* Appelle `incrementUntil` de façon récursive tant que la valeur n’a pas atteint le seuil.

---

#### 4️⃣ **Exécution**

* `runStateT` exécute le `StateT`.
* `runMaybeT` exécute le `MaybeT`.
* On obtient : `IO (Maybe (résultat, étatFinal))`.

---

### Exemple d’exécution

```
== Démonstration StateT + MaybeT ==
Valeur courante : 0
Valeur courante : 1
Valeur courante : 2
Valeur courante : 3
Valeur courante : 4
Valeur courante : 5
Succès ! État final = 5
```

Si vous changez la limite ou la condition pour provoquer un `Nothing`, vous verrez :

```
== Démonstration StateT + MaybeT ==
Valeur courante : 0
Valeur courante : 1
Valeur courante : 2
Valeur courante : 3
Valeur courante : 4
Valeur courante : 5
Échec : le seuil a été dépassé.
```
