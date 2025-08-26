## HC9T6 : Définir un type de données récursif

Définir un type de données récursif Tweet qui représente un tweet avec du contenu, des likes, et des commentaires (eux-mêmes des tweets).

---

Code haskell :

```haskell
-- Définition du type récursif Tweet
data Tweet = Tweet
  { content   :: String
  , likes     :: Int
  , comments  :: [Tweet]  -- liste de sous-tweets (commentaires)
  } deriving (Show)

-- Exemples d'utilisation
tweet1 :: Tweet
tweet1 = Tweet
  { content = "Bonjour tout le monde !"
  , likes = 5
  , comments = []
  }

tweet2 :: Tweet
tweet2 = Tweet
  { content = "Super post !"
  , likes = 3
  , comments = [tweet1]  -- tweet1 est un commentaire
  }

-- Programme principal
main :: IO ()
main = do
  print tweet1
  print tweet2
```

---

### 🔎 Explications

* `data Tweet = Tweet { ... }` : type en **record syntax**.
* `content :: String` → texte du tweet.
* `likes :: Int` → nombre de likes.
* `comments :: [Tweet]` → **liste de commentaires**, chacun étant un `Tweet`.
* C’est **récursif** : un tweet peut contenir d’autres tweets.
* `deriving (Show)` permet d’afficher les tweets directement.

---

### ✅ Résultat attendu

```
Tweet {content = "Bonjour tout le monde !", likes = 5, comments = []}
Tweet {content = "Super post !", likes = 3, comments = [Tweet {content = "Bonjour tout le monde !", likes = 5, comments = []}]}
```
