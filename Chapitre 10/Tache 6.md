## HC10T6 : Récursivité mutuelle dans Eq pour Blockchain

Modifier la classe Eq pour utiliser la récursivité mutuelle entre == et /= dans une instance pour le type Blockchain.

---

### Code haskell :

```haskell
-- Définition d'un type Blockchain simple
data Blockchain = Blockchain
  { chainName  :: String
  , blockCount :: Int
  } deriving (Show)

-- Instance Eq avec récursivité mutuelle
instance Eq Blockchain where
  b1 == b2 = blockCount b1 == blockCount b2 && chainName b1 == chainName b2
  b1 /= b2 = not (b1 == b2)

-- Exemples d'utilisation
bc1 :: Blockchain
bc1 = Blockchain "Bitcoin" 1000

bc2 :: Blockchain
bc2 = Blockchain "Ethereum" 1000

bc3 :: Blockchain
bc3 = Blockchain "Bitcoin" 1000

-- Programme principal
main :: IO ()
main = do
  print (bc1 == bc2)  -- False
  print (bc1 == bc3)  -- True
  print (bc1 /= bc2)  -- True
  print (bc1 /= bc3)  -- False
```

---

### 🔎 Explications

* `instance Eq Blockchain` : on fournit une **implémentation personnalisée** pour comparer deux blockchains.
* `==` : compare **le nombre de blocs** et le **nom de la chaîne**.
* `/=` : défini en termes de `==` : `b1 /= b2 = not (b1 == b2)` → **récursivité mutuelle**.
* Cette approche permet de **ne pas répéter la logique de comparaison** pour `/=`.

---

### ✅ Résultat attendu

```
False
True
True
False
```
