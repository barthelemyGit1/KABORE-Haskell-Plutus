## HC8T9 : Type enregistrement Transaction et fonction associée

Définir un type Transaction avec les champs from :: Address, to :: Address, amount :: Value, et transactionId :: String.

Définir une fonction createTransaction :: Address -> Address -> Value -> String qui crée une Transaction et retourne l’ID de la transaction.

### Code haskell

```haskell
-- Synonymes de type pour plus de clarté
type Address = String
type Value   = Int

-- Définition du type Transaction avec la syntaxe d’enregistrement
data Transaction = Transaction
  { from         :: Address
  , to           :: Address
  , amount       :: Value
  , transactionId :: String
  } deriving (Show)

-- Fonction qui crée une transaction et retourne son ID
createTransaction :: Address -> Address -> Value -> String
createTransaction fromAddr toAddr val =
  let tx = Transaction
            { from = fromAddr
            , to   = toAddr
            , amount = val
            , transactionId = "TX-" ++ fromAddr ++ "-" ++ toAddr ++ "-" ++ show val
            }
  in transactionId tx

-- Exemple d’utilisation
main :: IO ()
main = do
  let txId = createTransaction "Alice" "Bob" 100
  putStrLn ("Transaction créée avec ID : " ++ txId)
```

---

### 🔎 Explication

* `type Address = String`, `type Value = Int` → synonymes pour rendre le code plus expressif.
* `Transaction` est défini comme un **record** avec les champs `from`, `to`, `amount`, `transactionId`.
* `createTransaction` :

  * prend une adresse source, une adresse destination et une valeur,
  * construit une `Transaction` avec un ID simple généré à partir des données,
  * retourne l’ID (`transactionId tx`).
* `main` appelle la fonction pour tester.

---

### ✅ Résultat attendu

```
Transaction créée avec ID : TX-Alice-Bob-100
```
