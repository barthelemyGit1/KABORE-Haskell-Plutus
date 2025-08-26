## HC12T2 : Additionner deux nombres

Écrire une fonction addTwoNumbers qui prend deux entiers en entrée et retourne leur somme. Le résultat doit être affiché via la fonction main.

---

### Code haskell

```haskell
-- Définition de la fonction qui additionne deux nombres
addTwoNumbers :: Int -> Int -> Int
addTwoNumbers x y = x + y

-- Programme principal
main :: IO ()
main = do
  let a = 5
      b = 7
      result = addTwoNumbers a b
  putStrLn ("La somme de " ++ show a ++ " et " ++ show b ++ " est " ++ show result)
```

---

### 🔎 Explications

* `addTwoNumbers :: Int -> Int -> Int` : fonction qui prend deux entiers et retourne leur somme.
* `show` convertit un entier en chaîne de caractères pour l’afficher avec `putStrLn`.
* `main` définit deux nombres (`a` et `b`), calcule leur somme et l’affiche.

---

### ✅ Résultat attendu

```
La somme de 5 et 7 est 12
```
