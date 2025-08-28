## HC13T5 : Restreindre la visibilité dans le module

Refactoriser la fonction sumNonEmpty pour limiter la visibilité des fonctions utilitaires (comme les messages d’erreur) dans la liste d’exportation du module.

---
### Code haskell

### 1️⃣ Exemple : `SumNonEmpty.hs`

```haskell
module SumNonEmpty (sumNonEmpty) where
-- Seule sumNonEmpty est exportée, les fonctions internes restent privées

-- Fonction publique
sumNonEmpty :: Num a => [a] -> a
sumNonEmpty [] = emptyError
sumNonEmpty xs = sum xs

-- Fonction privée pour gérer le message d'erreur
emptyError :: a
emptyError = error "sumNonEmpty: liste vide"
```

---

### 2️⃣ Explications

1. **`module SumNonEmpty (sumNonEmpty) where`**

   * Seule `sumNonEmpty` est exportée.
   * `emptyError` **n’est pas listée** → elle est invisible depuis l’extérieur du module.

2. **Avantages**

   * L’API du module reste **propre et concise**.
   * Les détails internes (comme la gestion de l’erreur) ne sont pas accessibles au code utilisateur.
   * Tu peux changer `emptyError` plus tard sans impacter les utilisateurs du module.

3. **Usage dans `Main.hs`**

```haskell
import SumNonEmpty

main :: IO ()
main = do
    print $ sumNonEmpty [1,2,3]  -- affiche 6
    print $ sumNonEmpty []       -- provoque "sumNonEmpty: liste vide"
```
