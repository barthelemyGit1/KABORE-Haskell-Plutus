## Tâche 7 : Expressions booléennes

Écrivez des expressions booléennes qui évaluent à :

True en utilisant &&

False en utilisant ||

True en utilisant not

Une comparaison qui retourne False

---

## ✅ 1. **Une expression qui retourne `True` en utilisant `&&`**

```haskell
True && True
```

### 💬 Explication :

* `&&` est l'opérateur **ET logique** : il retourne `True` seulement si **les deux opérandes sont `True`**.
* Ici : `True && True` = `True`

---

## ✅ 2. **Une expression qui retourne `False` en utilisant `||`**

```haskell
False || False
```

### 💬 Explication :

* `||` est l'opérateur **OU logique** : il retourne `True` si **au moins un** des opérandes est `True`.
* Ici, les deux sont `False`, donc : `False || False` = `False`

---

## ✅ 3. **Une expression qui retourne `True` en utilisant `not`**

```haskell
not False
```

### 💬 Explication :

* `not` est l'opérateur de **négation logique**.
* Il inverse la valeur :

  * `not True` = `False`
  * `not False` = `True`
* Donc ici : `not False` = `True`

---

## ✅ 4. **Une comparaison qui retourne `False`**

```haskell
5 > 10
```

### 💬 Explication :

* `>` est un opérateur de comparaison : "supérieur à"
* Ici, `5` n’est pas supérieur à `10`, donc `5 > 10` = `False`

---

## ✅ Récapitulatif

| Expression     | Résultat | Opérateur utilisé |         |    |   |                 |
| -------------- | -------- | ----------------- | ------- | -- | - | --------------- |
| `True && True` | `True`   | `&&` (ET logique) |         |    |   |                 |
| \`False        |          | False\`           | `False` | \` |   | \` (OU logique) |
| `not False`    | `True`   | `not` (négation)  |         |    |   |                 |
| `5 > 10`       | `False`  | `>` (comparaison) |         |    |   |                 |

---

## 🔁 À tester dans GHCi

Tu peux ouvrir GHCi et taper :

```haskell
True && True
False || False
not False
5 > 10
```
