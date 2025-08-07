## Tâche 6 : Comprendre Int vs Integer

Définir une variable smallNumber de type Int avec la valeur 262.

Définir une variable bigNumber de type Integer avec la valeur 2127.

Essayez d’évaluer 2^64 :: Int dans GHCi et notez le résultat.

---

## ✅ 1. Définir la variable `smallNumber`

### 🔹 Code :

```haskell
smallNumber :: Int
smallNumber = 262
```

### 💬 Explication :

* `Int` est un entier **borné** (limité à une certaine plage).
* Sur la plupart des systèmes, `Int` représente des entiers **signés 64 bits** (valeurs entre `-2^63` et `2^63 - 1`).
* Ici, `262` est bien dans cette plage, donc aucun problème.

---

## ✅ 2. Définir la variable `bigNumber`

### 🔹 Code :

```haskell
bigNumber :: Integer
bigNumber = 2127
```

### 💬 Explication :

* `Integer` est un entier **arbitrairement grand** : il peut représenter des valeurs beaucoup plus grandes que `Int`.
* `2127` est un petit entier, mais on veut montrer que `Integer` accepte de très grandes valeurs **sans limite de taille (sauf mémoire)**.

---

## ✅ 3. Évaluer `2^64 :: Int` dans GHCi

### 🔹 Commande dans GHCi :

```haskell
2^64 :: Int
```

---

### ❗ Résultat :

Cela **dépend de ta machine**, mais typiquement sur GHC (64 bits), tu vas obtenir un **dépassement de capacité** (overflow).

#### Exemple typique du résultat :

```haskell
2^64 :: Int
-- Résultat : 0
```

Ou :

```haskell
2^64 :: Int
-- Résultat : -9223372036854775808
```

### 💥 Explication :

* `2^64 = 18,446,744,073,709,551,616` est **plus grand que la capacité maximale** de `Int` sur 64 bits (`2^63 - 1 = 9,223,372,036,854,775,807`)
* Donc, Haskell "enroule" (overflow) le résultat, ce qui donne une valeur incorrecte.
* Ce comportement est **dangereux** si on ne s’y attend pas !

---

### ✅ Solution correcte :

Si tu veux obtenir le bon résultat, utilise le type `Integer` :

```haskell
2^64 :: Integer
-- Résultat : 18446744073709551616
```

---

## 📄 Code complet :

```haskell
-- Définir des variables avec des types différents
smallNumber :: Int
smallNumber = 262

bigNumber :: Integer
bigNumber = 2127
```

---

## ✅ En résumé :

| Expression        | Type      | Résultat (GHCi)                     |
| ----------------- | --------- | ----------------------------------- |
| `smallNumber`     | `Int`     | `262`                               |
| `bigNumber`       | `Integer` | `2127`                              |
| `2^64 :: Int`     | `Int`     | **Overflow !** (résultat incorrect) |
| `2^64 :: Integer` | `Integer` | `18446744073709551616` (correct)    |

---
