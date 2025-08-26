## HC11T6 : AdvancedEq pour Blockchain

Définir une classe de type AdvancedEq qui étend Eq et ajoute une méthode compareEquality, puis l’implémenter pour le type Blockchain.

### Code haskell 

```haskell
-- Définition du type Blockchain
data Blockchain = Blockchain
  { chainName  :: String
  , blockCount :: Int
  } deriving (Show, Eq)

-- Définition de la sous-classe AdvancedEq
class Eq a => AdvancedEq a where
  compareEquality :: a -> a -> Bool

-- Implémentation de AdvancedEq pour Blockchain
instance AdvancedEq Blockchain where
  compareEquality b1 b2 = (chainName b1 == chainName b2) && (blockCount b1 == blockCount b2)

-- Exemples d'utilisation
bc1 :: Blockchain
bc1 = Blockchain "Bitcoin" 1000

bc2 :: Blockchain
bc2 = Blockchain "Ethereum" 1000

bc3 :: Blockchain
bc3 = Blockchain "Bitcoin" 1000

main :: IO ()
main = do
  print (compareEquality bc1 bc2)  -- False
  print (compareEquality bc1 bc3)  -- True
  print (bc1 == bc3)               -- True (utilise Eq)
  print (bc1 == bc2)               -- False (utilise Eq)
```

---

### 🔎 Explications

* `class Eq a => AdvancedEq a` :

  * `AdvancedEq` est une **sous-classe** de `Eq`.
  * Tout type `a` qui est `AdvancedEq` doit déjà être `Eq`.
* `compareEquality :: a -> a -> Bool` : méthode supplémentaire pour comparer deux éléments de façon personnalisée.
* Pour `Blockchain`, on compare **le nom de la chaîne** et le **nombre de blocs**.
* `==` reste disponible grâce à l’instance `Eq` déjà dérivée.

---

### ✅ Résultat attendu

```
False
True
True
False
```
