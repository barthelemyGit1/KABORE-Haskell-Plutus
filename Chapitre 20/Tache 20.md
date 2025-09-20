## HC20T20 : batchProcessing avec >>= (bind)

Écrire une fonction batchProcessing qui enchaîne plusieurs actions monadiques avec >>= (bind).

---

### Code haskell

```haskell
-- Exemple : traitement en batch sur des entiers avec IO

-- Fonction simple qui traite un entier
processItem :: Int -> IO Int
processItem x = do
    putStrLn $ "Traitement de l'élément : " ++ show x
    return (x * 2)  -- exemple : double la valeur

-- batchProcessing : enchaîne plusieurs actions monadiques avec >>
batchProcessing :: [Int] -> IO [Int]
batchProcessing [] = return []
batchProcessing (x:xs) =
    processItem x >>= \res ->       -- bind sur la première action
    batchProcessing xs >>= \rest -> -- bind sur le reste
    return (res : rest)             -- combine les résultats

-- -------- Programme principal -----------
main :: IO ()
main = do
    let items = [1,2,3,4,5]
    results <- batchProcessing items
    putStrLn $ "Résultats finaux : " ++ show results
```

---

### Explications

1. **`>>=` (bind)**  
   - Permet de **chaîner des actions monadiques**.  
   - La valeur produite par la première action est passée à une fonction qui retourne une action monadique suivante.

2. **`processItem`**  
   - Représente une opération sur un élément.  
   - Ici, on affiche l’élément et on retourne sa valeur doublée.

3. **`batchProcessing`**  
   - Cas de base : liste vide → `return []`.  
   - Cas récursif :  
     - Traite la tête `x` avec `processItem x`.  
     - Bind le résultat à `res`.  
     - Traite récursivement le reste `xs` avec `batchProcessing xs`.  
     - Bind le résultat à `rest`.  
     - Combine les deux (`res : rest`) et retourne.

4. **`main`**  
   - Applique `batchProcessing` à une liste `[1,2,3,4,5]`.  
   - Affiche le résultat final.

---

### Exemple d’exécution

```
Traitement de l'élément : 1
Traitement de l'élément : 2
Traitement de l'élément : 3
Traitement de l'élément : 4
Traitement de l'élément : 5
Résultats finaux : [2,4,6,8,10]
```

---

💡 **Résumé**  
- `>>=` est utilisé ici pour **enchaîner des calculs monadiques séquentiels**.  
- Chaque étape peut produire un effet (ici `IO`) et passer son résultat à l’étape suivante.  
- Cette technique fonctionne pour **IO**, **Maybe**, **State**, **Either**, etc.  
