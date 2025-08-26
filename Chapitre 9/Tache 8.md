## HC9T8 : Définir un type récursif Sequence

Définir un type de données récursif Sequence a représentant une séquence linéaire de nœuds, chacun contenant une valeur et pointant vers le nœud suivant.

---

### Code haskell :

```haskell
-- Type récursif Sequence a
data Sequence a
  = Empty                   -- fin de la séquence
  | Node a (Sequence a)     -- valeur et lien vers le suivant
  deriving (Show)

-- Exemples d'utilisation
seq1 :: Sequence Int
seq1 = Node 1 (Node 2 (Node 3 Empty))

seq2 :: Sequence String
seq2 = Node "A" (Node "B" (Node "C" Empty))

-- Programme principal
main :: IO ()
main = do
  print seq1  -- Node 1 (Node 2 (Node 3 Empty))
  print seq2  -- Node "A" (Node "B" (Node "C" Empty))
```

---

### 🔎 Explications

* `data Sequence a = Empty | Node a (Sequence a)` : type **récursif paramétrique**.

  * `Empty` représente la fin de la séquence.
  * `Node a (Sequence a)` contient une valeur `a` et un lien vers le prochain nœud.
* `deriving (Show)` permet d’afficher facilement les séquences.
* On peut créer des séquences de n’importe quel type (`Int`, `String`, etc.).

---

### ✅ Résultat attendu

```
Node 1 (Node 2 (Node 3 Empty))
Node "A" (Node "B" (Node "C" Empty))
```
