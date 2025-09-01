## HC19T6 : Fonction repeatEffect avec forever

Définir la fonction repeatEffect qui exécute indéfiniment un effet avec forever.

---

### 1. Type de la fonction

```haskell
repeatEffect :: IO a -> IO b
```

* La fonction prend une action `IO a` et retourne une action `IO b` (en pratique, elle ne termine jamais, donc `b` n’a pas vraiment d’importance).

---

### 2. Utilisation de `forever`

`forever` vient de `Control.Monad` :

```haskell
forever :: Monad m => m a -> m b
```

* Elle exécute **l’action donnée à l’infini**.

---

### 3. Implémentation

```haskell
import Control.Monad (forever)

repeatEffect :: IO a -> IO b
repeatEffect action = forever action
```

* Simple, clair et concis.
* `forever action` répète `action` indéfiniment.

---

### 4. Exemple d’utilisation

```haskell
main :: IO ()
main = repeatEffect $ do
  putStrLn "Salut !"
  putStrLn "Je vais me répéter à l’infini..."
```

---

### Explication

`forever`

Répète l’action donnée indéfiniment.

`repeatEffect action = forever action`

La fonction prend une action `IO` et la répète pour toujours.

---
Résultat : le programme affichera en boucle les deux lignes jusqu’à ce que l'on interrompe le programme (Ctrl+C).
