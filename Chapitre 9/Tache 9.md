## HC9T9 : Vérifier la présence d’un élément dans une Sequence

Créer une fonction elemSeq qui vérifie si un élément donné est présent dans une Sequence.

---

### Code Haskell :

```haskell
-- Type Sequence déjà défini
data Sequence a
  = Empty
  | Node a (Sequence a)
  deriving (Show)

-- Fonction qui vérifie si un élément est dans la séquence
elemSeq :: Eq a => a -> Sequence a -> Bool
elemSeq _ Empty = False
elemSeq x (Node val next)
  | x == val  = True
  | otherwise = elemSeq x next

-- Exemples d'utilisation
seq1 :: Sequence Int
seq1 = Node 1 (Node 2 (Node 3 Empty))

seq2 :: Sequence String
seq2 = Node "A" (Node "B" (Node "C" Empty))

-- Programme principal
main :: IO ()
main = do
  print (elemSeq 2 seq1)      -- True
  print (elemSeq 4 seq1)      -- False
  print (elemSeq "B" seq2)    -- True
  print (elemSeq "D" seq2)    -- False
```

---

### 🔎 Explications

* `elemSeq :: Eq a => a -> Sequence a -> Bool`

  * `Eq a =>` : le type `a` doit être comparable (`==`).
* `elemSeq _ Empty = False` → si la séquence est vide, l’élément n’est pas présent.
* `elemSeq x (Node val next)` :

  * si `x == val`, retourne `True`.
  * sinon, continue à chercher dans le reste de la séquence (`next`).
* La fonction **parcourt toute la séquence** jusqu’à trouver l’élément ou atteindre la fin.

---

### ✅ Résultat attendu

```
True
False
True
False
```
