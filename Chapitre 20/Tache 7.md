## HC20T7 : findFirst avec la monade Either

Créer une fonction findFirst qui utilise la monade Either pour gérer les erreurs lors de la recherche d’un élément dans une liste.

---

## Code haskell

```haskell
-- On importe find de Data.List pour rechercher un élément
import Data.List (find)

-- findFirst : prend un prédicat et une liste,
-- renvoie Either String a
--   - Right a si un élément est trouvé
--   - Left "message d'erreur" sinon
findFirst :: (a -> Bool) -> [a] -> Either String a
findFirst p xs =
  case find p xs of
    Just val -> Right val
    Nothing  -> Left "Aucun élément ne correspond au prédicat."

main :: IO ()
main = do
  print $ findFirst even [1,3,5,8,9]     -- Right 8
  print $ findFirst (>10) [1,3,5,8,9]    -- Left "Aucun élément ne correspond au prédicat."
```

---

💡 **Explications :**

* `Either e a` est une monade pratique pour représenter :

  * `Left e` → une erreur (ici une `String`)
  * `Right a` → une valeur correcte.
* On utilise `Data.List.find` pour récupérer le premier élément qui satisfait le prédicat.
* Si `find` renvoie `Nothing`, on transforme cela en `Left` avec un message d’erreur clair.
