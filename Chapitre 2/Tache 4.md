Tâche 4 : Notation préfixe et infixe
## Utilisez la notation préfixe pour les expressions suivantes :

5 + 3
10 * 4
True && False
## Utilisez la notation infixe pour les fonctions suivantes :

(+) 7 2
(*) 6 5
(&&) True False

---

En Haskell, il existe **deux façons d’appeler des fonctions ou opérateurs** :

* La **notation infixe** (comme en mathématiques) : `5 + 3`
* La **notation préfixe** (comme en programmation fonctionnelle) : ` (+) 5 3`

Tu peux **utiliser les deux** en Haskell, car **les opérateurs sont des fonctions**.

---

## ✅ 1. **Utiliser la notation **préfixe** pour les expressions suivantes**

On transforme les opérateurs en fonctions en **les plaçant entre parenthèses**.

### 🔹 a) `5 + 3`

* **Infixe :** `5 + 3`
* **Préfixe :** `(+) 5 3`

#### 💬 Explication :

* L’opérateur `+` est une **fonction binaire**.
* En notation préfixe, tu écris la fonction suivie de ses deux arguments : `f x y`.
* Ici : `+` devient `(+)`, et on applique à `5` et `3`.

---

### 🔹 b) `10 * 4`

* **Infixe :** `10 * 4`
* **Préfixe :** `(*) 10 4`

---

### 🔹 c) `True && False`

* **Infixe :** `True && False`
* **Préfixe :** `(&&) True False`

#### 💬 Remarque :

* `&&` est une fonction logique qui prend deux `Bool`.

---

## ✅ 2. **Utiliser la notation **infixe** pour les fonctions suivantes**

On transforme les fonctions en opérateurs en les mettant **entre backticks \` \`**.

### 🔹 a) `(+) 7 2`

* **Préfixe :** `(+) 7 2`
* **Infixe :** `7 + 2`

---

### 🔹 b) `(*) 6 5`

* **Préfixe :** `(*) 6 5`
* **Infixe :** `6 * 5`

---

### 🔹 c) `(&&) True False`

* **Préfixe :** `(&&) True False`
* **Infixe :** `True && False`

---

## 🔁 Récapitulatif

| Expression Infixe | Équivalent Préfixe |
| ----------------- | ------------------ |
| `5 + 3`           | `(+) 5 3`          |
| `10 * 4`          | `(*) 10 4`         |
| `True && False`   | `(&&) True False`  |

| Expression Préfixe | Équivalent Infixe |
| ------------------ | ----------------- |
| `(+) 7 2`          | `7 + 2`           |
| `(*) 6 5`          | `6 * 5`           |
| `(&&) True False`  | `True && False`   |

---
