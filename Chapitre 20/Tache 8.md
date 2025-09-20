## HC20T8 : Parser monadique pour des expressions simples
Construire un parseur qui analyse des expressions simples en utilisant la monade Parser. Donne moi un code avec un main pour tester. Suivi d'explication du code

---

## Code haskell

```haskell
{-# LANGUAGE BlockArguments #-}

import Text.ParserCombinators.ReadP
import Control.Applicative ((<|>))

-- Définition du parseur d'expressions arithmétiques

-- Un nombre : séquence de chiffres
number :: ReadP Double
number = do
  skipSpaces
  n <- munch1 (`elem` "0123456789.")
  return (read n)

-- Facteur : soit un nombre, soit une expression entre parenthèses
factor :: ReadP Double
factor =
      number
  <|> between (char '(' >> skipSpaces) (skipSpaces >> char ')') expr

-- Terme : multiplication ou division
term :: ReadP Double
term = chainl1 factor op
  where
    op = (skipSpaces >> char '*' >> skipSpaces >> return (*))
     <|> (skipSpaces >> char '/' >> skipSpaces >> return (/))

-- Expression : addition ou soustraction
expr :: ReadP Double
expr = chainl1 term op
  where
    op = (skipSpaces >> char '+' >> skipSpaces >> return (+))
     <|> (skipSpaces >> char '-' >> skipSpaces >> return (-))

-- Fonction utilitaire pour lancer le parseur
parseExpr :: String -> Either String Double
parseExpr input =
  case readP_to_S (expr <* skipSpaces <* eof) input of
    [(res, "")] -> Right res
    _           -> Left "Erreur de syntaxe dans l'expression."

-- -------- Programme principal --------

main :: IO ()
main = do
  putStrLn "Tapez une expression arithmétique (ex: 2 + 3 * (4 - 1)) :"
  line <- getLine
  case parseExpr line of
    Right val -> putStrLn $ "Résultat = " ++ show val
    Left err  -> putStrLn $ "Erreur : " ++ err
```

---

### Explication

1. **Bibliothèque `ReadP`**

   * `ReadP` est un type de parseur fourni par `Text.ParserCombinators.ReadP`.
   * C’est une monade, donc on peut combiner les parseurs avec `do`, `<|>`, etc.

2. **Structure du parseur :**

   * `number` : lit un flottant (on accepte aussi les décimales).
   * `factor` : lit soit un `number`, soit une expression entre parenthèses (via `between`).
   * `term` : gère `*` et `/` en utilisant `chainl1`, qui applique une opération de gauche à droite.
   * `expr` : gère `+` et `-`, toujours avec `chainl1`.

3. **Gestion des espaces**

   * `skipSpaces` est utilisé à chaque étape pour ignorer les espaces inutiles.

4. **Fonction `parseExpr`**

   * `readP_to_S` exécute le parseur.
   * On exige que toute l’entrée soit consommée (`eof`).
   * On renvoie un `Either` : `Right résultat` si tout est bon, `Left` si l’analyse échoue.

5. **`main`**

   * Demande une expression à l’utilisateur.
   * Appelle `parseExpr` et affiche soit le résultat, soit le message d’erreur.

---

📌 **Exemples d’exécution :**

```
Tapez une expression arithmétique (ex: 2 + 3 * (4 - 1)) :
2 + 3 * (4 - 1)
Résultat = 11.0
```

```
Tapez une expression arithmétique (ex: 2 + 3 * (4 - 1)) :
5 / (2 - 2)
Résultat = Infinity
```

```
Tapez une expression arithmétique (ex: 2 + 3 * (4 - 1)) :
2 + *
Erreur : Erreur de syntaxe dans l'expression.
```
