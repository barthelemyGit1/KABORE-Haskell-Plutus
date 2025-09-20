## HC20T16 : retryIO avec la monade IO

Définir une fonction retryIO qui réessaie une opération IO un nombre spécifié de fois avec la monade IO.

---

### Code haskell

```haskell
import Control.Exception (SomeException, try)
import Control.Monad (when)

-- retryIO : réessaie une opération IO jusqu'à n fois en cas d'échec
retryIO :: Int -> IO a -> IO (Maybe a)
retryIO 0 _ = return Nothing  -- plus de tentatives
retryIO n action = do
    result <- try action       -- capture les exceptions
    case result of
      Right val -> return (Just val)       -- succès
      Left  (_ :: SomeException) -> do
          putStrLn $ "Échec, " ++ show (n-1) ++ " tentative(s) restante(s)..."
          retryIO (n-1) action            -- réessaie
          
-- -------- Programme principal -----------
main :: IO ()
main = do
    let action = do
          putStrLn "Taper un nombre (0 pour échouer) :"
          n <- readLn
          if n == 0 then error "Erreur simulée" else return n
    result <- retryIO 3 action
    case result of
      Just val -> putStrLn $ "Succès : " ++ show val
      Nothing  -> putStrLn "Toutes les tentatives ont échoué."
```

---

## Explications

1. **`try`**

   * Permet de capturer les exceptions dans une opération IO.
   * Renvoie `Right val` si tout va bien, ou `Left e` si une exception survient.

2. **Récursivité**

   * Si `n == 0`, on renvoie `Nothing` → plus de tentatives.
   * Sinon, on exécute `action`.

     * Succès → `Just val`
     * Échec → affiche un message et réessaie avec `n-1`.

3. **Type final**

```haskell
retryIO :: Int -> IO a -> IO (Maybe a)
```

* `Maybe a` indique si l’opération a fini par réussir (`Just`) ou échoué (`Nothing`) après toutes les tentatives.

4. **Exemple d’exécution**

```
Taper un nombre (0 pour échouer) :
0
Échec, 2 tentative(s) restante(s)...
Taper un nombre (0 pour échouer) :
0
Échec, 1 tentative(s) restante(s)...
Taper un nombre (0 pour échouer) :
5
Succès : 5
```

---

💡 **Remarque :**

* Cette version gère **toutes les exceptions** (`SomeException`).
* On peut facilement adapter `retryIO` pour ne capturer que certaines exceptions spécifiques.
