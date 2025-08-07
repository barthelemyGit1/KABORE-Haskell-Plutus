Tâche 1 : Vérification des types dans GHCi
Ouvrez GHCi et vérifiez les types des expressions suivantes :

---

### 1. `42`

* **Type attendu :** `Integer` ou `Num a => a`
  (GHCi retourne le type générique `Num a => a` car `42` peut être utilisé comme n'importe quel type numérique)

* **Commande GHCi :**

  ```haskell
  :t 42
  ```

---

### 2. `3.14`

* **Type attendu :** `Fractional a => a`
  (`3.14` est un nombre à virgule flottante, donc il est de type `Fractional`)

* **Commande GHCi :**

  ```haskell
  :t 3.14
  ```

---

### 3. `"Haskell"`

* **Type attendu :** `String`
  (`String` est un synonyme pour `[Char]`, une liste de caractères)

* **Commande GHCi :**

  ```haskell
  :t "Haskell"
  ```

---

### 4. `'Z'`

* **Type attendu :** `Char`
  (C’est un caractère unique entre apostrophes)

* **Commande GHCi :**

  ```haskell
  :t 'Z'
  ```

---

### 5. `True && False`

* **Type attendu :** `Bool`
  (L'opérateur `&&` prend deux `Bool` et retourne un `Bool`)

* **Commande GHCi :**

  ```haskell
  :t True && False
  ```

---

### Résumé des types attendus :

| Expression      | Type attendu        |
| --------------- | ------------------- |
| `42`            | `Num a => a`        |
| `3.14`          | `Fractional a => a` |
| `"Haskell"`     | `String`            |
| `'Z'`           | `Char`              |
| `True && False` | `Bool`              |

