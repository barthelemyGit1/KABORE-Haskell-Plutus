## HC20T15 : treeSum avec une monade personnalisée

Écrire une fonction treeSum qui calcule la somme des éléments d’un arbre binaire à l’aide d’une monade personnalisée.

---

### 1️⃣ Définition de l’arbre

```haskell
-- Arbre binaire simple
data Tree a = Empty
            | Node a (Tree a) (Tree a)
            deriving (Show)
```

---

### 2️⃣ Définition d’une monade personnalisée

Ici, on définit une monade `SumM` qui encapsule un calcul de somme.

```haskell
-- Monade personnalisée pour accumuler une somme
newtype SumM a = SumM { runSumM :: (a, Int) }  -- a : valeur calculée, Int : somme accumulée

instance Functor SumM where
    fmap f (SumM (x, s)) = SumM (f x, s)

instance Applicative SumM where
    pure x = SumM (x, 0)
    (SumM (f, s1)) <*> (SumM (x, s2)) = SumM (f x, s1 + s2)

instance Monad SumM where
    return = pure
    (SumM (x, s1)) >>= f =
        let SumM (y, s2) = f x
        in SumM (y, s1 + s2)

-- Fonction pour ajouter une valeur à la somme
addSum :: Int -> SumM ()
addSum n = SumM ((), n)
```

---

### 3️⃣ Calcul de la somme de l’arbre avec la monade

```haskell
treeSum :: Tree Int -> SumM Int
treeSum Empty = return 0
treeSum (Node x left right) = do
    addSum x           -- ajouter la valeur du noeud à la somme
    l <- treeSum left
    r <- treeSum right
    return (x + l + r)  -- retourne la somme locale
```

---

### 4️⃣ Exemple d’utilisation

```haskell
main :: IO ()
main = do
    let tree = Node 5
                  (Node 3 (Node 1 Empty Empty) (Node 4 Empty Empty))
                  (Node 8 Empty (Node 10 Empty Empty))
        SumM (_, total) = treeSum tree
    putStrLn $ "La somme des éléments de l'arbre est : " ++ show total
```

---

### Explications

1. **`SumM`**

   * Une monade personnalisée qui transporte une **somme accumulée**.
   * Le champ `Int` stocke la somme totale des valeurs ajoutées via `addSum`.

2. **`addSum`**

   * Ajoute une valeur à l’accumulateur de somme sans affecter la valeur calculée.

3. **`treeSum`**

   * Parcourt l’arbre en profondeur.
   * Pour chaque `Node`, ajoute la valeur du noeud à la somme avec `addSum`.
   * Combine les résultats des sous-arbres.

4. **Résultat final**

   * Dans `main`, on extrait la somme via `runSumM`.

---

### Exemple de sortie

Pour l’arbre donné :

```
La somme des éléments de l'arbre est : 31
```

---

💡 **Remarque**
Cette approche montre comment créer une **monade personnalisée pour un effet spécifique** (ici, l’accumulation de somme) et l’utiliser dans un calcul récursif sur une structure de données comme un arbre.
