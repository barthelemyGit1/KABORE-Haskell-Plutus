## HC3T10 - Tâche avancée 10 : Vérifier si une chaîne est un palindrome (récursion, gardes)

Définir isPalindrome :: String -> Bool.

Utiliser des gardes :

Si la chaîne a 0 ou 1 caractère : True

Si le premier et le dernier caractère correspondent, vérifier récursivement le reste.

Sinon, retourner False.

Tester avec isPalindrome "racecar", isPalindrome "haskell" et isPalindrome "madam".

---

## ✅ Code Haskell

```haskell
-- Fonction isPalindrome
isPalindrome :: String -> Bool
isPalindrome str
    | length str <= 1 = True
    | head str == last str = isPalindrome (init (tail str))
    | otherwise = False

-- Fonction principale pour tester
main :: IO ()
main = do
    print (isPalindrome "racecar") -- True
    print (isPalindrome "haskell") -- False
    print (isPalindrome "madam")   -- True
```

---

## 🧠 Explication

1. **Signature**

   ```haskell
   isPalindrome :: String -> Bool
   ```

   La fonction prend une chaîne (`String`) et retourne un booléen (`Bool`).

2. **Gardes**

   * `| length str <= 1 = True`
     Une chaîne vide ou avec un seul caractère est toujours un palindrome.

   * `| head str == last str = isPalindrome (init (tail str))`
     Si le **premier caractère** (`head`) et le **dernier caractère** (`last`) sont égaux, on vérifie récursivement l’intérieur de la chaîne (`init (tail str)`).

   * `| otherwise = False`
     Si la première et la dernière lettre sont différentes → pas un palindrome.

3. **Tests**

   * `"racecar"` → `True` ✅
   * `"haskell"` → `False` ✅
   * `"madam"` → `True` ✅

---
