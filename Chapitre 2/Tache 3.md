Définir les variables immuables suivantes en Haskell :

myAge comme un Int
piValue comme un Double
greeting comme un String
isHaskellFun comme un Bool
Essayez de modifier l’une des variables et observez le résultat.

---

### ✅ Définition des variables immuables :

```haskell
-- Âge (nombre entier)
myAge :: Int
myAge = 25

-- Valeur de pi (nombre flottant)
piValue :: Double
piValue = 3.14159

-- Message de bienvenue
greeting :: String
greeting = "Bonjour, Haskell !"

-- Est-ce que Haskell est amusant ?
isHaskellFun :: Bool
isHaskellFun = True
```

---

### ✅ Explication :

* `myAge :: Int` signifie que `myAge` est de type entier.
* `piValue :: Double` désigne un nombre à virgule flottante en double précision.
* `greeting :: String` est une chaîne de caractères.
* `isHaskellFun :: Bool` est un booléen (vrai ou faux).

> Une fois ces définitions faites, **on ne peut plus redéfinir les mêmes noms** dans le même contexte. Sinon, Haskell générera une **erreur**.

---

### 🔁 Essayons de modifier une variable

Supposons que tu tapes ce qui suit dans GHCi après avoir défini `myAge` :

```haskell
myAge = 30
```

### 💥 Résultat dans GHCi :

```haskell
error:
    Multiple declarations of ‘myAge’
    It was previously defined at <interactive>:1:1
```

➡️ Cela signifie que **la variable `myAge` a déjà été définie** et que tu **ne peux pas la redéfinir**.

---

### 💡 Pourquoi c’est utile ?

Cette **immutabilité** rend Haskell **plus sûr**, surtout en programmation fonctionnelle. Une variable qui ne change pas évite les erreurs liées aux effets de bord et rend le raisonnement sur le code plus simple.

---

### ✅ Résumé :

| Variable       | Type     | Valeur                 |
| -------------- | -------- | ---------------------- |
| `myAge`        | `Int`    | `25`                   |
| `piValue`      | `Double` | `3.14159`              |
| `greeting`     | `String` | `"Bonjour, Haskell !"` |
| `isHaskellFun` | `Bool`   | `True`                 |

---
