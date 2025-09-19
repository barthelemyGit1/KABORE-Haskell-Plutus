## HC20T5 : Configurer les messages de salutation avec la monade Reader

Utiliser la monade Reader pour créer un système de configuration pour saluer les utilisateurs.

---

## Code Haskell

```haskell
import Control.Monad.Reader

-- | Configuration pour les messages de salutation
data Config = Config
  { greeting :: String   -- message de base ("Bonjour", "Hello", ...)
  , punctuation :: String -- ponctuation finale ("!", " :) ", etc.)
  }

-- | Fonction qui lit la configuration et salue un utilisateur
sayHello :: String -> Reader Config String
sayHello name = do
  cfg <- ask  -- Récupère la configuration
  return $ greeting cfg ++ " " ++ name ++ punctuation cfg

-- | Exemple d'utilisation
main :: IO ()
main = do
  let config1 = Config { greeting = "Bonjour", punctuation = " !" }
      config2 = Config { greeting = "Hello", punctuation = " :)" }

  putStrLn "=== Avec config1 ==="
  putStrLn $ runReader (sayHello "Alice") config1
  putStrLn $ runReader (sayHello "Bob") config1

  putStrLn "\n=== Avec config2 ==="
  putStrLn $ runReader (sayHello "Charlie") config2
  putStrLn $ runReader (sayHello "Diana") config2
```

---

## Explication

1. **Définition de la configuration**

   ```haskell
   data Config = Config
     { greeting :: String
     , punctuation :: String
     }
   ```

   * Elle contient les paramètres du message : texte de salutation et ponctuation.

2. **Monade Reader**

   * `Reader Config` représente un calcul qui a accès à une configuration partagée.

3. **Fonction `sayHello`**

   * Utilise `ask` pour lire la configuration courante.
   * Construit le message en fonction du `greeting` et de `punctuation`.

4. **`runReader`**

   * Permet d’exécuter le calcul en lui passant une configuration donnée.

---

### Exemple de sortie

```
=== Avec config1 ===
Bonjour Alice !
Bonjour Bob !

=== Avec config2 ===
Hello Charlie :)
Hello Diana :)
```

---

💡 **À retenir :**
La monade **Reader** est idéale quand tu veux partager un contexte immuable (comme une config ou des paramètres globaux) entre plusieurs fonctions sans le passer explicitement en argument.
