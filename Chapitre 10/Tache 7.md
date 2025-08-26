## HC10T7 : Classe de type Convertible
Créer une classe de type Convertible avec convert :: a -> b.
L’implémenter pour la conversion de PaymentMethod en String.

---

### Code haskell

```haskell
-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency deriving (Show)

-- Définition de la classe de type Convertible
class Convertible a b where
  convert :: a -> b

-- Implémentation de Convertible pour PaymentMethod -> String
instance Convertible PaymentMethod String where
  convert Cash           = "Paiement en espèces"
  convert Card           = "Paiement par carte"
  convert Cryptocurrency = "Paiement en crypto-monnaie"

-- Exemples d'utilisation
main :: IO ()
main = do
  putStrLn (convert Cash)
  putStrLn (convert Card)
  putStrLn (convert Cryptocurrency)
```

---

### 🔎 Explications

* `class Convertible a b where convert :: a -> b` : définit une **interface** pour convertir un type `a` en un type `b`.
* `instance Convertible PaymentMethod String` : implémente cette interface pour convertir un `PaymentMethod` en `String`.
* Chaque constructeur (`Cash`, `Card`, `Cryptocurrency`) est transformé en **chaîne lisible**.

---

### ✅ Résultat attendu

```
Paiement en espèces
Paiement par carte
Paiement en crypto-monnaie
```
