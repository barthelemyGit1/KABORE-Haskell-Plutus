## HC20T9 : replicateMonad avec la monade Identity
 
Implémenter une fonction replicateMonad qui réplique une valeur en utilisant la monade Identity.

---

### Code haskell

```haskell
import Control.Monad.Identity

-- replicateMonad : réplique une valeur dans la monade Identity
replicateMonad :: Int -> a -> Identity [a]
replicateMonad n x = do
  return (replicate n x)

-- -------- Programme principal --------
main :: IO ()
main = do
  let r1 = runIdentity (replicateMonad 5 "Bonjour")
      r2 = runIdentity (replicateMonad 3 (42 :: Int))
  putStrLn $ "r1 = " ++ show r1
  putStrLn $ "r2 = " ++ show r2
```

---

### Explications

1. **`Identity`**

   * `Identity` est une monade très simple, qui ne fait “rien” de spécial :

     ```haskell
     newtype Identity a = Identity { runIdentity :: a }
     ```
   * C’est pratique pour tester des fonctions monadiques sans effets particuliers.

2. **`replicateMonad`**

   * Signature :

     ```haskell
     replicateMonad :: Int -> a -> Identity [a]
     ```
   * Elle prend :

     * un entier `n` : le nombre de répétitions,
     * une valeur `x` : l’élément à dupliquer,
     * et renvoie une liste de `x` dans la monade `Identity`.

3. **Utilisation**

   * `runIdentity` “extrait” la valeur hors de la monade pour l’afficher.
   * On obtient bien des listes ordinaires.

---

📌 **Exécution attendue :**

```
r1 = ["Bonjour","Bonjour","Bonjour","Bonjour","Bonjour"]
r2 = [42,42,42]
```
