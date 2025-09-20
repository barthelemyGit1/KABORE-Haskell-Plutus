## HC20T17 : validatePassword avec la monade Either

Implémenter une fonction validatePassword qui effectue plusieurs vérifications avec la monade Either pour retourner les erreurs de validation.

---

### Code complet

```haskell
import Data.Char (isUpper, isLower, isDigit)

-- Type d'erreur pour la validation
type ValidationError = String

-- validatePassword : vérifie plusieurs règles et retourne Right si ok ou Left si erreur
validatePassword :: String -> Either ValidationError String
validatePassword pwd = do
    checkLength pwd
    checkUpper pwd
    checkLower pwd
    checkDigit pwd
    return pwd

-- Vérification de la longueur minimale
checkLength :: String -> Either ValidationError ()
checkLength s
    | length s < 8 = Left "Le mot de passe doit contenir au moins 8 caractères."
    | otherwise    = Right ()

-- Vérifie qu'il y a au moins une majuscule
checkUpper :: String -> Either ValidationError ()
checkUpper s
    | any isUpper s = Right ()
    | otherwise     = Left "Le mot de passe doit contenir au moins une lettre majuscule."

-- Vérifie qu'il y a au moins une minuscule
checkLower :: String -> Either ValidationError ()
checkLower s
    | any isLower s = Right ()
    | otherwise     = Left "Le mot de passe doit contenir au moins une lettre minuscule."

-- Vérifie qu'il y a au moins un chiffre
checkDigit :: String -> Either ValidationError ()
checkDigit s
    | any isDigit s = Right ()
    | otherwise     = Left "Le mot de passe doit contenir au moins un chiffre."

-- -------- Programme principal --------
main :: IO ()
main = do
    putStrLn "Entrez un mot de passe :"
    pwd <- getLine
    case validatePassword pwd of
      Right _  -> putStrLn "Mot de passe valide !"
      Left err -> putStrLn $ "Mot de passe invalide : " ++ err
```

---

### Explications

1. **Monade `Either`**

   * `Left error` : représente une erreur de validation.
   * `Right value` : mot de passe valide.

2. **Règles de validation**

   * `checkLength` → au moins 8 caractères.
   * `checkUpper` → au moins une majuscule.
   * `checkLower` → au moins une minuscule.
   * `checkDigit` → au moins un chiffre.

3. **Séquence des validations**

   * En utilisant la monade `Either`, la première erreur arrête immédiatement la validation.
   * Si toutes passent → `Right pwd`.

---

### Exemple d’exécution

```
Entrez un mot de passe :
abc
Mot de passe invalide : Le mot de passe doit contenir au moins 8 caractères.
```

```
Entrez un mot de passe :
Abcdefgh
Mot de passe invalide : Le mot de passe doit contenir au moins un chiffre.
```

```
Entrez un mot de passe :
Abcdefg1
Mot de passe valide !
```

---

💡 **Remarque :**

* L’approche `Either` est idéale pour **enchaîner des validations séquentielles** et retourner la **première erreur rencontrée**.
* Pour accumuler toutes les erreurs, il faudrait utiliser un **type `Validation`** ou `Either [String] a`.
