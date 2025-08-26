## HC9T7 : Fonction pour calculer l’engagement

Créer une fonction engagement qui calcule l’engagement d’un Tweet en sommant ses likes et l’engagement de ses commentaires.

---

Code Haskell :

```haskell
-- Type Tweet déjà défini
data Tweet = Tweet
  { content  :: String
  , likes    :: Int
  , comments :: [Tweet]
  } deriving (Show)

-- Fonction qui calcule l'engagement total d'un Tweet
engagement :: Tweet -> Int
engagement (Tweet _ likes comments) =
  likes + sum (map engagement comments)

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
  putStrLn ("Engagement tweet1 : " ++ show (engagement tweet1))  -- 5
  putStrLn ("Engagement tweet2 : " ++ show (engagement tweet2))  -- 8
```

---

### 🔎 Explications

* `engagement (Tweet _ likes comments)` : on ignore le contenu avec `_`.
* `likes` → nombre de likes du tweet principal.
* `sum (map engagement comments)` → applique récursivement `engagement` sur chaque commentaire et somme les résultats.
* Cette fonction **parcourt toute la hiérarchie** des commentaires, quelle que soit la profondeur.

---

### ✅ Résultat attendu

```
Engagement tweet1 : 5
Engagement tweet2 : 8
```
