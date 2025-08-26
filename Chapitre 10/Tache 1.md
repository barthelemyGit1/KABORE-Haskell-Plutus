## HC10T1 : Classe de type ShowSimple

Définir une nouvelle classe de type ShowSimple qui exige une fonction showSimple :: a -> String pour une conversion simple en chaîne de caractères.

Implémenter une instance pour le type PaymentMethod.

---

Code Haskell complet :

```haskell
-- Définition du type PaymentMethod
data PaymentMethod = Cash | Card | Cryptocurrency deriving (Show)

-- Définition de la classe de type ShowSimple
class ShowSimple a where
  showSimple :: a -> String

-- Implémentation de ShowSimple pour PaymentMethod
instance ShowSimple PaymentMethod where
  showSimple Cash           = "Paiement en espèces"
  showSimple Card           = "Paiement par carte"
  showSimple Cryptocurrency = "Paiement en crypto-monnaie"

-- Exemples d'utilisation
main :: IO ()
main = do
  putStrLn (showSimple Cash)
  putStrLn (showSimple Card)
  putStrLn (showSimple Cryptocurrency)
```

---

### 🔎 Explications

* `class ShowSimple a where ...` : définit une **interface** avec une fonction `showSimple`.
* `instance ShowSimple PaymentMethod where ...` : implémente cette interface pour le type `PaymentMethod`.
* Chaque constructeur (`Cash`, `Card`, `Cryptocurrency`) est converti en **chaîne lisible**.

---

### ✅ Résultat attendu

```
Paiement en espèces
Paiement par carte
Paiement en crypto-monnaie
```
