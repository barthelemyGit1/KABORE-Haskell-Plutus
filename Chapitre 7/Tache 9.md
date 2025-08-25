## HC7T9 : Définir une classe de type avec plusieurs instances 

Créer une classe de type Describable avec une méthode describe.

L’implémenter pour Bool et Shape.

---

### Code Haskell

```haskell
-- Définition du type Shape
data Shape = Circle Double | Rectangle Double Double
    deriving (Show)

-- Définition de la classe de type Describable
class Describable a where
    describe :: a -> String

-- Instance pour Bool
instance Describable Bool where
    describe True  = "C'est vrai"
    describe False = "C'est faux"

-- Instance pour Shape
instance Describable Shape where
    describe (Circle r)      = "Cercle de rayon " ++ show r
    describe (Rectangle w h) = "Rectangle de largeur " ++ show w ++ " et hauteur " ++ show h

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ describe True                     -- "C'est vrai"
    print $ describe False                    -- "C'est faux"
    print $ describe (Circle 5.0)            -- "Cercle de rayon 5.0"
    print $ describe (Rectangle 3.0 4.0)    -- "Rectangle de largeur 3.0 et hauteur 4.0"
```

---

### Explications

1. **Classe de type**

   ```haskell
   class Describable a where
       describe :: a -> String
   ```

   * `Describable` est une **interface générique**.
   * Tout type `a` qui est instance de `Describable` doit implémenter `describe`.

2. **Instance Bool**

   ```haskell
   describe True  = "C'est vrai"
   describe False = "C'est faux"
   ```

   * On décrit simplement les valeurs booléennes.

3. **Instance Shape**

   ```haskell
   describe (Circle r)      = "Cercle de rayon " ++ show r
   describe (Rectangle w h) = "Rectangle de largeur " ++ show w ++ " et hauteur " ++ show h
   ```

   * On fournit une **description textuelle** pour chaque constructeur.

4. **Tests**

   * Fonctionne avec `Bool` et `Shape`.
   * Retourne toujours une `String`.

---

### Exemple de sortie

```
"C'est vrai"
"C'est faux"
"Cercle de rayon 5.0"
"Rectangle de largeur 3.0 et hauteur 4.0"
```

---

💡 Astuce : Cette approche permet de créer des **interfaces réutilisables** pour tout type personnalisé.
