## HC11T8 : Dérivation de Eq et Ord pour PaymentMethod

Dériver les instances Eq et Ord pour PaymentMethod et tester les comparaisons.

---

### Code haskell

```haskell
-- Définition du type PaymentMethod avec dérivation Eq et Ord
data PaymentMethod = Cash | Card | Cryptocurrency
  deriving (Show, Eq, Ord)

-- Exemples d'utilisation
main :: IO ()
main = do
  let pm1 = Cash
      pm2 = Card
      pm3 = Cryptocurrency

  -- Comparaisons avec Eq
  print (pm1 == pm2)   -- False
  print (pm1 /= pm2)   -- True
  print (pm1 == Cash)  -- True

  -- Comparaisons avec Ord
  print (pm1 < pm2)    -- True (selon l'ordre de déclaration)
  print (pm3 > pm2)    -- True
  print (min pm1 pm3)  -- Cash
  print (max pm1 pm3)  -- Cryptocurrency
```

---

### 🔎 Explications

* `deriving (Eq, Ord)` : Haskell génère automatiquement les instances `Eq` et `Ord`.

  * `Eq` permet `==` et `/=`.
  * `Ord` permet `<`, `>`, `<=`, `>=`, `min`, `max`.
* L’ordre dans `Ord` suit **l’ordre de déclaration des constructeurs** : `Cash < Card < Cryptocurrency`.

---

### ✅ Résultat attendu

```
False
True
True
True
True
Cash
Cryptocurrency
```
