## HC20T19 : Système de journalisation avec la monade Writer

Implémenter un système de journalisation basé sur la monade Writer pour tracer les appels de fonctions et leurs arguments.

---

### Code haskell

```haskell
import Control.Monad.Writer

-- Type alias pour notre Writer
-- String contient le journal
type Logger a = Writer [String] a

-- Fonction simple avec journalisation
add :: Int -> Int -> Logger Int
add x y = do
    tell ["add appelé avec arguments : " ++ show x ++ ", " ++ show y]
    return (x + y)

multiply :: Int -> Int -> Logger Int
multiply x y = do
    tell ["multiply appelé avec arguments : " ++ show x ++ ", " ++ show y]
    return (x * y)

-- Chaîne d'opérations avec journalisation
compute :: Logger Int
compute = do
    a <- add 3 4
    b <- multiply a 10
    c <- add b 5
    return c

-- -------- Programme principal -----------
main :: IO ()
main = do
    let (result, logLines) = runWriter compute
    putStrLn $ "Résultat final : " ++ show result
    putStrLn "\nJournal des opérations :"
    mapM_ putStrLn logLines
```

---

## Explications

1. **`Writer`**

   * Monade qui transporte un **résultat** et un **journal** en même temps.
   * Ici, on utilise `[String]` pour accumuler les messages.

2. **`tell`**

   * Ajoute un message dans le journal sans modifier le résultat principal.
   * Exemple : `tell ["add appelé avec arguments : 3, 4"]`

3. **Combinaison des opérations**

   * Les fonctions `add` et `multiply` retournent un résultat **normal** (`Int`) tout en accumulant des messages.
   * Dans `compute`, chaque étape ajoute automatiquement son journal à celui des étapes précédentes.

4. **`runWriter`**

   * Extrait le résultat final et le journal associé.
   * Signature : `runWriter :: Writer w a -> (a, w)`

---

### Exemple d’exécution

```
Résultat final : 75

Journal des opérations :
add appelé avec arguments : 3, 4
multiply appelé avec arguments : 7, 10
add appelé avec arguments : 70, 5
```

---

💡 **Résumé**

* La monade `Writer` est idéale pour **tracer des appels et accumuler des logs**.
* Chaque fonction ajoute ses messages via `tell`, ce qui évite d’avoir à gérer manuellement une liste de logs.
* On peut remplacer `[String]` par d’autres types monoidaux (comme `Text` ou des compteurs) pour différents styles de journalisation.
