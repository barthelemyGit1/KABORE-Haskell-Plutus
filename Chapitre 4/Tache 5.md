## HC4T5 - Tâche 5 : Ajouter un cas générique avec un message personnalisé

Modifier specialBirthday pour inclure l'âge dans le message si l’âge ne correspond pas à un cas prédéfini.

---

### Code Haskell avec message personnalisé

```haskell
-- Fonction qui retourne un message spécial selon l'âge
specialBirthday :: Int -> String
specialBirthday 0  = "Bienvenue dans ce monde !"
specialBirthday 18 = "Félicitations pour ta majorité !"
specialBirthday 50 = "Joyeux anniversaire !"
specialBirthday age = "Bon anniversaire pour tes " ++ show age ++ " ans !"

-- Fonction principale pour tester
main :: IO ()
main = do
    print $ specialBirthday 0
    print $ specialBirthday 18
    print $ specialBirthday 50
    print $ specialBirthday 30
    print $ specialBirthday 7
```

---

### Explications

1. **Pattern matching** :

   * `0`, `18`, `50` → cas spéciaux avec messages fixes.
   * `age` → correspond à **tous les autres âges** (au lieu de `_`) et permet d’utiliser cette valeur dans le message.

2. **Utilisation de `show`** :

   * Convertit l’entier `age` en chaîne de caractères pour pouvoir concaténer avec `"Bon anniversaire pour tes "`.

3. **Pureté** :

   * `specialBirthday` reste une **fonction pure**, car le résultat dépend uniquement de l’âge donné.

---

### Exemple de sortie

```
"Bienvenue dans ce monde !"
"Félicitations pour ta majorité !"
"Joyeux anniversaire !"
"Bon anniversaire pour tes 30 ans !"
"Bon anniversaire pour tes 7 ans !"
```
