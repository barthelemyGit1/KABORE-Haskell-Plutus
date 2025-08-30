## HC16T7: Vérifier la présence d'un élément dans une liste

Ecrire une fonction qui vérifie si un élément existe dans une liste.

---

## 🔹 Version simplifiée avec `elem`

```haskell
module Main where

main :: IO ()
main = do
    let liste = [1, 2, 3, 4, 5]
    putStrLn $ "Est-ce que 3 est dans la liste ? " ++ show (3 `elem` liste)
    putStrLn $ "Est-ce que 7 est dans la liste ? " ++ show (7 `elem` liste)
```

---

## 📝 Explication

* **`elem`** est une fonction déjà définie dans le Prelude :

  ```haskell
  elem :: Eq a => a -> [a] -> Bool
  ```

  Elle fait exactement ce qu’on avait codé manuellement :

  * prend un élément,
  * une liste,
  * renvoie `True` s’il est présent, `False` sinon.

* Avec la syntaxe infixe :

  ```haskell
  3 `elem` [1,2,3,4,5]   -- True
  7 `elem` [1,2,3,4,5]   -- False
  ```
