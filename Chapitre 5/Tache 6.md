## HC5T6 : Composition de fonctions

Utiliser la composition (.) pour créer une fonction qui prend une liste de nombres et retourne leurs carrés filtrés pour ne garder que les pairs.

---

### Code Haskell

```haskell
-- Fonction qui retourne les carrés pairs d'une liste
squaredEvens :: [Int] -> [Int]
squaredEvens = filter even . map (^2)

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ squaredEvens [1,2,3,4,5]   -- [4,16]
    print $ squaredEvens [0,7,8]       -- [0,64]
    print $ squaredEvens []            -- []
```

---

### Explications

1. **Composition `(.)`**

   ```haskell
   squaredEvens = filter even . map (^2)
   ```

   * `map (^2)` → élève chaque nombre au carré.
   * `filter even` → garde seulement les nombres pairs.
   * `(filter even . map (^2))` → équivalent à `\xs -> filter even (map (^2) xs)`
     → c’est la **composition de fonctions** : le résultat de `map (^2)` est passé directement à `filter even`.

2. **Avantages**

   * Fonction **pure** et concise.
   * Lisibilité : on voit directement le flux “données → carré → filtrage des pairs”.

---

### Exemple de sortie

```
[4,16]
[0,64]
[]
```
