## HC13T2 : Filtrer les fichiers par sous-chaîne
Écrire une fonction qui filtre les fichiers du répertoire courant selon une sous-chaîne présente dans le nom du fichier à l’aide de Data.List.isInfixOf.

---

### Code haskell
```haskell
import System.Directory (listDirectory, doesDirectoryExist)
import System.FilePath ((</>))
import Data.List (isInfixOf)

-- Liste uniquement les fichiers (comme dans l'exercice précédent, version sans filterM)
listFiles :: FilePath -> IO [FilePath]
listFiles path = do
    items <- System.Directory.listDirectory path
    files <- mapM (\item -> do
                        isDir <- System.Directory.doesDirectoryExist (path </> item)
                        return (item, isDir)) items
    return [name | (name, isDir) <- files, not isDir]

-- Filtrer les fichiers qui contiennent une sous-chaîne
filterFilesBySubstring :: String -> [FilePath] -> [FilePath]
filterFilesBySubstring substring = filter (isInfixOf substring)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez une sous-chaine pour filtrer les fichiers :"
    substring <- getLine
    files <- listFiles "."
    let filtered = filterFilesBySubstring substring files
    putStrLn "Fichiers correspondants :"
    mapM_ putStrLn filtered
```

---

### 🔎 Explications

* `isInfixOf substring file` → vrai si `substring` apparaît dans `file`.
* `filter (isInfixOf substring) files` → garde uniquement les fichiers contenant la sous-chaîne.
* Exemple : si tu as les fichiers `note.txt`, `data.csv`, `important_note.doc`, et tu entres `"note"`, il affichera :

  ```
  note.txt
  important_note.doc
  ```

---
