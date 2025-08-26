## HC9T1 : Définir un synonyme de type paramétrique 

Créer un synonyme de type paramétrique appelé Entity a pour représenter différents types d’entités avec des adresses.

---

### Code haskell
```haskell
-- Synonyme de type paramétrique
type Address = String
type Entity a = (a, Address)  -- une entité de type 'a' avec une adresse

-- Exemples d’utilisation
personEntity :: Entity String
personEntity = ("Alice", "123 Rue Principale")

companyEntity :: Entity String
companyEntity = ("ACME Corp", "456 Avenue Centrale")

-- Programme principal
main :: IO ()
main = do
  print personEntity
  print companyEntity
```

---

### 🔎 Explications :

* `type Entity a = (a, Address)`

  * crée un alias `Entity` **paramétré** par un type `a`.
  * Chaque `Entity a` est un **tuple** `(a, Address)` où `a` peut être n’importe quel type (ex: `String`, `Int`, etc.)
* `personEntity` est une `Entity String` : une personne avec un nom et une adresse.
* `companyEntity` est aussi une `Entity String` : une entreprise avec un nom et une adresse.

---

### ✅ Résultat attendu

```
("Alice","123 Rue Principale")
("ACME Corp","456 Avenue Centrale")
```

Si tu veux, je peux te montrer comment définir une **Entity paramétrique avec un record** au lieu d’un tuple pour rendre les champs plus explicites. Veux‑tu que je fasse ça ?
