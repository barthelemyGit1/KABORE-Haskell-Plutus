## HC4T6 - Tâche 6 : Identifier le contenu d'une liste par pattern matching
Créer une fonction whatsInsideThisList qui retourne une chaîne selon le nombre d’éléments dans la liste.

---

### Code Haskell

```haskell
-- Fonction qui décrit le contenu d'une liste selon sa taille
whatsInsideThisList :: [a] -> String
whatsInsideThisList []        = "La liste est vide."
whatsInsideThisList [_]       = "La liste contient un seul élément."
whatsInsideThisList [_, _]    = "La liste contient deux éléments."
whatsInsideThisList (x:xs)    = "La liste contient plus de deux éléments."

-- Fonction principale pour tester
main :: IO ()
main = do
    putStrLn $ whatsInsideThisList []
    putStrLn $ whatsInsideThisList [1]
    putStrLn $ whatsInsideThisList [1, 2]
    putStrLn $ whatsInsideThisList [1, 2, 3]
    putStrLn $ whatsInsideThisList ["a", "b", "c", "d"]
```

---

### Explications

1. **Pattern matching sur les listes** :

   * `[]` → liste vide.
   * `[_]` → liste avec un seul élément (`_` signifie “je ne m’intéresse pas à sa valeur”).
   * `[_, _]` → liste avec exactement deux éléments.
   * `(x:xs)` → liste avec **au moins un élément** et un reste `xs` → ici, plus de deux éléments.

2. **Fonction pure** :

   * `whatsInsideThisList` ne dépend que de l’argument fourni et n’a pas d’effets de bord.

3. **Fonction `main`** :

   * Teste plusieurs listes pour illustrer les différents cas.
   * Utilise `putStrLn` pour afficher le résultat.

---

### Exemple de sortie

```
La liste est vide.
La liste contient un seul élément.
La liste contient deux éléments.
La liste contient plus de deux éléments.
La liste contient plus de deux éléments.
```
