## HC13T3 : Trier et retourner les fichiers filtrés

Implémenter une fonction qui trie et retourne les noms de fichiers filtrés du répertoire courant en utilisant Data.List.sort et Data.List.filter.

---

### Code haskell

Ici on va combiner **`Data.List.filter`** et **`Data.List.sort`** pour :

1. Récupérer les fichiers du répertoire courant
2. Filtrer selon une sous-chaîne donnée
3. Trier le résultat par ordre alphabétique

---

### ✅ Code complet `Tache3.hs`

```haskell
import System.Directory (listDirectory, doesDirectoryExist)
import System.FilePath ((</>))
import Data.List (isInfixOf, sort)

-- Fonction pour lister uniquement les fichiers (pas les dossiers)
listFiles :: FilePath -> IO [FilePath]
listFiles path = do
    items <- listDirectory path
    files <- mapM (\item -> do
                        isDir <- doesDirectoryExist (path </> item)
                        return (item, isDir)) items
    return [name | (name, isDir) <- files, not isDir]

-- Filtrer et trier les fichiers
filterAndSortFiles :: String -> [FilePath] -> [FilePath]
filterAndSortFiles substring files =
    sort (filter (isInfixOf substring) files)

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Enter a substring to filter files:"
    substring <- getLine
    files <- listFiles "."
    let result = filterAndSortFiles substring files
    putStrLn "Filtered and sorted files:"
    mapM_ putStrLn result
```

---

### 🔎 Explications

* `listFiles "."` → récupère seulement les fichiers du répertoire courant.
* `filter (isInfixOf substring) files` → garde ceux qui contiennent la sous-chaîne.
* `sort (...)` → trie les résultats par ordre alphabétique.

---

### 💡 Exemple

Si le répertoire contient :

```
data.csv
report.txt
notes.md
readme.txt
```

et que tu entres `"t"`, le programme affichera :

```
notes.md
readme.txt
report.txt
```
