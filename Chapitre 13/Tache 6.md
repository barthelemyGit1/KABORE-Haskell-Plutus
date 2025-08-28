## HC13T6 : Convertir des fichiers filtrés en map

Créer une fonction qui utilise Data.Map pour convertir une liste de noms de fichiers filtrés en une map clé/valeur.

---

### Code haskell

Pour l’exemple, on peut faire :

* clé = nom du fichier
* valeur = longueur du nom du fichier (ou tout autre attribut que tu veux)

---

### 1️⃣ Code complet

```haskell
import System.Directory (listDirectory, doesDirectoryExist)
import System.FilePath ((</>))
import Data.List (isInfixOf)
import qualified Data.Map as Map  -- On importe Data.Map qualifié
import Data.Map (Map)

-- Lister uniquement les fichiers
listFiles :: FilePath -> IO [FilePath]
listFiles path = do
    items <- listDirectory path
    files <- mapM (\item -> do
                        isDir <- doesDirectoryExist (path </> item)
                        return (item, isDir)) items
    return [name | (name, isDir) <- files, not isDir]

-- Filtrer les fichiers par sous-chaîne
filterFiles :: String -> [FilePath] -> [FilePath]
filterFiles substring files = filter (isInfixOf substring) files

-- Convertir une liste de fichiers en Map clé/valeur
filesToMap :: [FilePath] -> Map FilePath Int
filesToMap files = Map.fromList [(f, length f) | f <- files]
-- Ici la valeur est la longueur du nom du fichier

-- Fonction principale
main :: IO ()
main = do
    putStrLn "Entrez une sous-chaîne pour filtrer les fichiers :"
    substring <- getLine
    files <- listFiles "."
    let filtered = filterFiles substring files
    let fileMap = filesToMap filtered
    putStrLn "Map des fichiers filtrés (clé = nom, valeur = longueur) :"
    mapM_ print (Map.toList fileMap)
```

---

### 2️⃣ Explications

1. `Map.fromList [(f, length f) | f <- files]`

   * Transforme la liste en `Map` où chaque fichier devient une **clé**, et la **valeur** est ici la longueur du nom.

2. `Map.toList fileMap`

   * Pour afficher la map, on la convertit en liste de paires `(clé, valeur)`.

3. Utilisation possible :

   * On pourrait remplacer `length f` par **taille du fichier**, date de modification, etc.
