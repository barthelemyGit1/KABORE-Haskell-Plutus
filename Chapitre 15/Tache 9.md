## HC15T9 : Utiliser try pour intercepter les exceptions IO de fichier

Utiliser la fonction try pour capturer les exceptions IO liées aux fichiers et les gérer élégamment.

---

## ✅ Exemple complet avec `try` et gestion d’erreurs IO

```haskell
module Main where

import System.IO
import Control.Exception (try, IOException)

main :: IO ()
main = do
    putStrLn "Entrez le nom du fichier à lire :"
    fileName <- getLine

    -- On capture les exceptions liées au fichier
    result <- try (readFile fileName) :: IO (Either IOException String)

    case result of
        Left e   -> putStrLn $ "Erreur lors de la lecture du fichier : " ++ show e
        Right content -> do
            putStrLn "Contenu du fichier :"
            putStrLn content
```

---

## ⚡ Explications

* `try (readFile fileName)` tente d’ouvrir et lire le fichier.
* Si une **erreur IO** survient (ex : fichier inexistant) → retourne `Left IOException`.
* Si tout se passe bien → retourne `Right contenu`.

---

### 💡 Exemple d’exécution

```
Entrez le nom du fichier à lire :
test.txt
Contenu du fichier :
Bonjour Haskell !
```

Si le fichier n’existe pas :

```
Entrez le nom du fichier à lire :
notfound.txt
Erreur lors de la lecture du fichier : notfound.txt: openFile: does not exist (No such file or directory)
```
