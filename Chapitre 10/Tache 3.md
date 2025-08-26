## HC10T3 : Classe de type Comparable

Définir une classe de type Comparable avec une fonction compareWith :: a -> a -> Ordering.

L’implémenter pour Blockchain.

---

### Code haskell

```haskell
-- Définition d'un type Blockchain simple
data Blockchain = Blockchain
  { chainName :: String
  , blockCount :: Int
  } deriving (Show)

-- Définition de la classe de type Comparable
class Comparable a where
  compareWith :: a -> a -> Ordering

-- Implémentation de Comparable pour Blockchain
instance Comparable Blockchain where
  compareWith b1 b2 = compare (blockCount b1) (blockCount b2)

-- Exemples d'utilisation
bc1 :: Blockchain
bc1 = Blockchain "Bitcoin" 1000

bc2 :: Blockchain
bc2 = Blockchain "Ethereum" 500

-- Programme principal
main :: IO ()
main = do
  print (compareWith bc1 bc2)  -- GT
  print (compareWith bc2 bc1)  -- LT
  print (compareWith bc1 bc1)  -- EQ
```

---

### 🔎 Explications

* `class Comparable a where compareWith :: a -> a -> Ordering` : définit une **interface** pour comparer deux valeurs.
* `instance Comparable Blockchain where ...` : pour `Blockchain`, on compare **le nombre de blocs** (`blockCount`).
* `compare :: Ord b => b -> b -> Ordering` renvoie :

  * `LT` si le premier est plus petit,
  * `GT` si le premier est plus grand,
  * `EQ` si les deux sont égaux.
* `Blockchain` a deux champs : `chainName` et `blockCount`.

---

### ✅ Résultat attendu

```
GT
LT
EQ
```
