## HC19T9 : Démonstration de pureAndApply

Implémenter pureAndApply pour démontrer l’utilisation de pure avec des

---

### 1. Idée générale

* `pure` **élève** une valeur « normale » dans un conteneur/applicatif.
* Ensuite, on peut utiliser `<*>` pour **appliquer une fonction dans ce contexte** à une autre valeur dans le même contexte.

---

### 2. Exemple avec `Maybe`

```haskell
pureAndApply :: Maybe Int
pureAndApply = pure (+3) <*> Just 7
```

### Explication

1. `pure (+3)`

   * Élève la fonction `(+3)` dans le contexte `Maybe`.
   * Résultat : `Just (+3)`

2. `<*> Just 7`

   * Applique la fonction contenue dans `Just (+3)` à la valeur contenue dans `Just 7`.
   * Résultat final : `Just 10`

---

### 3. Exemple plus général avec `IO`

```haskell
pureAndApplyIO :: IO Int
pureAndApplyIO = pure (+5) <*> (return 20)
```

* `pure (+5)` dans `IO` devient `return (+5)`
* `return 20` est le deuxième argument.
* `<*>` applique la fonction à la valeur dans le contexte `IO`.
* Quand on exécute `pureAndApplyIO`, on obtient `25` dans `IO` :

```haskell
main :: IO ()
main = do
  result <- pureAndApplyIO
  print result   -- Affiche 25
```

---

### 4. Récapitulatif de l’idée

| Opérateur | Usage                                                                     | Exemple                          |
| --------- | ------------------------------------------------------------------------- | -------------------------------- |
| `pure`    | Élève une valeur/fonction dans un contexte applicatif                     | `pure 7 :: Maybe Int == Just 7`  |
| `<*>`     | Applique une fonction dans le contexte à une valeur dans le même contexte | `Just (+3) <*> Just 4 == Just 7` |

---

✅ Avec `pureAndApply`, tu vois **clairement comment `pure` et `<*>` fonctionnent ensemble**.
