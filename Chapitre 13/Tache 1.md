## HC13T1 : Lister les fichiers du répertoire courant

Créer un programme qui liste tous les fichiers du répertoire courant en utilisant le module System.Directory.

---

### Code haskell

```haskell
import System.Directory (listDirectory, doesDirectoryExist)
import System.FilePath ((</>))

-- Fonction pour lister uniquement les fichiers (sans filterM)
listFiles :: FilePath -> IO [FilePath]
listFiles path = do
    items <- listDirectory path
    -- Vérifie chaque item : garde seulement si ce n'est pas un dossier
    files <- mapM (\item -> do
                        isDir <- doesDirectoryExist (path </> item)
                        return (item, isDir)) items
    return [name | (name, isDir) <- files, not isDir]

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Fichiers du répertoire courant :"
    files <- listFiles "."
    mapM_ putStrLn files
```

---

### 🔎 Explications

1. `listDirectory "."` → liste tous les éléments (fichiers **et** dossiers) du répertoire courant.
2. `doesDirectoryExist` → permet de filtrer pour ne garder que les **fichiers**.
3. `filterM` → applique un filtre monadique (ici `IO Bool`).
4. `mapM_ putStrLn files` → affiche chaque fichier sur une nouvelle ligne.

---
