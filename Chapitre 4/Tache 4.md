## HC4T4 - Tâche 4 : Réécrire specialBirthday avec le pattern matching

Réécrire la fonction specialBirthday en utilisant le pattern matching au lieu des if-else.

---

### Exemple : fonction qui retourne un message spécial selon l’âge

#### Version `if-else` typique

```haskell
specialBirthday :: Int -> String
specialBirthday age =
    if age == 0 then "Bienvenue dans ce monde !"
    else if age == 18 then "Félicitations pour ta majorité !"
    else if age == 50 then "Joyeux 50 ans !"
    else "Bon anniversaire !"
```

---

### Réécriture avec **pattern matching**

```haskell
specialBirthday :: Int -> String
specialBirthday 0  = "Bienvenue dans ce monde !"
specialBirthday 18 = "Félicitations pour ta majorité !"
specialBirthday 50 = "Joyeux 50 ans !"
specialBirthday _  = "Bon anniversaire !"


-- Funtion prinpipale
main :: IO ()
main = do 
  print ("age  0 : " ++ specialBirthday  0)
  print ("age 10 : " ++ specialBirthday 10)
  print ("age 30 :" ++ specialBirthday 30)
  print ("age 50 :" ++ specialBirthday 50)
  print ("age 100 :" ++ specialBirthday 100)
  
```

---

### Explications

1. **Pattern matching** :

   * Chaque valeur spécifique d’âge (`0`, `18`, `50`) a sa propre ligne.
   * `_` correspond à **tous les autres cas**, équivalent du `else` dans l’`if-else`.

2. **Avantages** :

   * Le code est plus lisible et plus concis.
   * Plus facile à étendre si tu veux ajouter d’autres âges spéciaux.

---

**Sortie :**

```
"age  0 : Bienvenue dans ce monde !"
"age 10 : Bon anniversaire !"
"age 30 :Bon anniversaire !"
"age 50 :Joyeux 50 ans !"
"age 100 :Bon anniversaire !"

```
