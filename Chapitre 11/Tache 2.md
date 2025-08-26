## HC11T2 : Fonction fancyFunction pour WeAccept

Implémenter la fonction fancyFunction pour la classe WeAccept et la tester avec différents types comme Cardano, Cash et Country.

---

### Code haskell

```haskell
-- Définition de la classe de type WeAccept
class WeAccept a where
  fancyFunction :: a -> String

-- Définition de types simples
data Cardano = Cardano deriving (Show)
data Cash = Cash deriving (Show)
data Country = Country String deriving (Show)

-- Instances WeAccept pour ces types
instance WeAccept Cardano where
  fancyFunction _ = "Nous acceptons Cardano !"

instance WeAccept Cash where
  fancyFunction _ = "Nous acceptons les paiements en espèces !"

instance WeAccept Country where
  fancyFunction (Country name) = "Pays accepté : " ++ name

-- Programme principal pour tester
main :: IO ()
main = do
  putStrLn (fancyFunction Cardano)
  putStrLn (fancyFunction Cash)
  putStrLn (fancyFunction (Country "Burkina Faso"))
```

---

### 🔎 Explications

* `class WeAccept a where fancyFunction :: a -> String` : interface qui définit une fonction personnalisée pour chaque type.
* Chaque type (`Cardano`, `Cash`, `Country`) a sa propre implémentation de `fancyFunction`.
* `Country` est paramétré avec un nom, qu’on concatène dans la chaîne de sortie.

---

### ✅ Résultat attendu

```
Nous acceptons Cardano !
Nous acceptons les paiements en espèces !
Pays accepté : Burkina Faso
```
