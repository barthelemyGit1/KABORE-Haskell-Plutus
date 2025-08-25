## HC4T1 - Tâche 1 : Définir une fonction weatherReport

Créer une fonction weatherReport :: String -> String qui prend une condition météo (par exemple, « sunny », « rainy », « cloudy ») et retourne un message décrivant le temps.

Utiliser le pattern matching pour traiter les cas suivants :

« sunny » → « Il fait beau et ensoleillé ! »

« rainy » → « N'oublie pas ton parapluie ! »

« cloudy » → « Un peu gris, mais pas de pluie pour l'instant ! »

Toute autre entrée doit retourner « Météo inconnue ».

---

### Code Haskell

```haskell
-- Fonction qui renvoie un message selon la météo
weatherReport :: String -> String
weatherReport "sunny"  = "Il fait beau et ensoleillé !"
weatherReport "rainy"  = "N'oublie pas ton parapluie !"
weatherReport "cloudy" = "Un peu gris, mais pas de pluie pour l'instant !"
weatherReport _        = "Météo inconnue"

-- Fonction principale
main :: IO ()
main = do
    input = "sunny"               -- Affecte la valeur sunny a la variable input
    let report = weatherReport input -- Appeler la fonction pure
    putStrLn report                 -- Afficher le résultat
```
---

### Explications

1. **La fonction `weatherReport`**

   ```haskell
   weatherReport :: String -> String
   ```

   * Elle prend une chaîne (`String`) en entrée et renvoie une chaîne (`String`) en sortie.
   * **Pattern matching** :

     * `"sunny"` → `"Il fait beau et ensoleillé !"`.
     * `"rainy"` → `"N'oublie pas ton parapluie !"`.
     * `"cloudy"` → `"Un peu gris, mais pas de pluie pour l'instant !"`.
     * `_` (underscore) → correspond à **toute autre valeur** → `"Météo inconnue"`.

   👉 C’est une fonction **pure** : pas d’entrées/sorties, résultat toujours déterminé par l’entrée.

2. **La fonction `main`**

   ```haskell
   main :: IO ()
   ```

   * `IO ()` : type des fonctions principales qui font des entrées/sorties.
   * `putStrLn "..."` : affiche un message à l’écran.
   * `getLine` : attend que l’utilisateur entre du texte et le retourne sous forme de `String`.
   * `let report = weatherReport input` : on passe l’entrée à la fonction pure.
   * `putStrLn report` : affiche le message correspondant.

---
