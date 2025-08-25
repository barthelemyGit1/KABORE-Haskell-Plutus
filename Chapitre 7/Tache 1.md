## HC7T1 : Implémenter une instance Eq pour un type personnalisé

Définir un type de données Color représentant Red, Green et Blue.

Implémenter la classe de type Eq afin que deux couleurs du même type soient considérées égales.

---

### Code Haskell

```haskell
-- Définition d'un type Color
data Color = Red | Green | Blue

-- Implémentation de l'instance Eq pour Color
instance Eq Color where
    Red   == Red   = True
    Green == Green = True
    Blue  == Blue  = True
    _     == _     = False

-- Fonction principale pour tester
main :: IO ()
main = do
    print (Red == Red)     -- True
    print (Red == Green)   -- False
    print (Blue == Blue)   -- True
    print (Green == Blue)  -- False
```

---

### Explications

1. **Définition du type**

   ```haskell
   data Color = Red | Green | Blue
   ```

   * On crée un **type algébrique** `Color` avec 3 valeurs possibles.

2. **Classe de type `Eq`**

   ```haskell
   instance Eq Color where ...
   ```

   * On dit à Haskell **comment comparer deux couleurs**.

3. **Cas d’égalité**

   * Si les deux couleurs sont identiques (`Red == Red`, etc.) → `True`.
   * Sinon (`_ == _`) → `False`.

4. **Test**

   * On peut maintenant utiliser `==` directement sur nos couleurs.

---

### Exemple de sortie

```
True
False
True
False
```

---

Sache que Haskell peut aussi **dériver automatiquement** l’instance `Eq` :

```haskell
data Color = Red | Green | Blue deriving (Eq, Show)
```
