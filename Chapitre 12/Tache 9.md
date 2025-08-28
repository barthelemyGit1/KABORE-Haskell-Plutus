## HC12T9 : Lire et afficher le contenu d’un fichier

Écrire un programme qui lit un fichier et affiche son contenu dans le terminal. Gérer les erreurs si le fichier n’existe pas.

---

### Code haskell

```haskell
import System.IO
import System.IO.Error (catchIOError)

-- Fonction pour lire et afficher le fichier
readAndPrintFile :: FilePath -> IO ()
readAndPrintFile fileName = catchIOError
    (do
        contents <- readFile fileName
        putStrLn "Contenu du fichier :"
        putStrLn contents
    )
    (\e -> putStrLn $ "Erreur : impossible de lire le fichier. " ++ show e)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez le nom du fichier à lire :"
    fileName <- getLine
    readAndPrintFile fileName
```

---

### Explications :

1. **Lecture du fichier** :

   ```haskell
   contents <- readFile fileName
   ```

   lit tout le contenu du fichier en une seule chaîne de caractères.

2. **Gestion des erreurs** :

   * `catchIOError` capture les exceptions (ex. fichier inexistant).
   * On affiche un message d’erreur avec `show e`.

3. **Interaction utilisateur** :

   * Demande le nom du fichier avec `getLine`.
   * Appelle `readAndPrintFile` pour lire et afficher.

---
