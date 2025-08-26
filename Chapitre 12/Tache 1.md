## HC12T1 : Afficher un message de bienvenue

Créer un programme Haskell qui affiche « Bienvenue dans la programmation Haskell ! » dans le terminal.

---

### Code haskell

```haskell
-- Fichier : Main.hs

main :: IO ()
main = putStrLn "Bienvenue dans la programmation Haskell !"
```

---

### 🔎 Explications

* `main :: IO ()` : point d’entrée principal d’un programme Haskell.
* `putStrLn` : affiche une chaîne de caractères dans le terminal et ajoute un retour à la ligne.

---

### ✅ Résultat attendu dans le terminal

```
Bienvenue dans la programmation Haskell !
```
