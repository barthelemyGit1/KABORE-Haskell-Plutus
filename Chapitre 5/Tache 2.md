## HC5T2 : Filtrer les nombres impairs

Utiliser la fonction filter pour extraire tous les nombres impairs d’une liste d’entiers de 1 à 30.

---

### Code Haskell

```haskell
-- Fonction pour filtrer les nombres impairs
oddNumbers :: [Int] -> [Int]
oddNumbers xs = filter odd xs

-- Fonction principale pour tester
main :: IO ()
main = do
    let numbers = [1..30]          -- Liste des entiers de 1 à 30
    print $ oddNumbers numbers
```

---

### Explications

1. **`filter`**

   ```haskell
   filter odd xs
   ```

   * `filter` prend une **fonction booléenne** (`odd`) et une liste `xs`.
   * Elle renvoie une **nouvelle liste** ne contenant que les éléments pour lesquels la fonction retourne `True`.
   * `odd` est une fonction prédéfinie qui retourne `True` si un nombre est impair.

2. **Liste `[1..30]`**

   * Crée tous les entiers de 1 à 30.

3. **Pureté**

   * `oddNumbers` est une **fonction pure** : le résultat dépend uniquement de sa liste d’entrée.

---

### Exemple de sortie

```
[1,3,5,7,9,11,13,15,17,19,21,23,25,27,29]
```
