## HC19T8 : Fonction discardSecond avec <*

Implémenter une fonction discardSecond qui utilise l’opérateur <* pour retourner le premier argument après séquencement des effets.

---

### 1. Rappel : `<*`

```haskell
(<*) :: Applicative f => f a -> f b -> f a
```

* Exécute les deux effets.
* Retourne uniquement le **résultat du premier**.
* Exemple avec `IO` :

```haskell
putStrLn "A" <* putStrLn "B"
-- Affiche "A" puis "B", retourne ()
```

---

### 2. Définition de la fonction

```haskell
discardSecond :: IO a -> IO b -> IO a
discardSecond io1 io2 = io1 <* io2
```

### Explication

1. `discardSecond :: IO a -> IO b -> IO a`

   * La fonction prend **deux actions `IO`**.
   * Elle retourne le **résultat du premier** après exécution des deux.

2. `io1 <* io2`

   * Exécute `io1`, puis `io2`.
   * Retourne le résultat de `io1`.

---

### 3. Exemple d’utilisation

```haskell
main :: IO ()
main = do
  result <- discardSecond
              (putStrLn "Première action" >> return 10)
              (putStrLn "Deuxième action" >> return 20)
  print result
```

**Résultat à l’écran :**

```
Première action
Deuxième action
10
```

* Les deux `putStrLn` s’exécutent dans l’ordre.
* La valeur retournée est `10` (celle de la première action), et non `20`.
