# Partie 1 : Setup

## Création d'un utilisateur dans le domaine  
Pour créer un deuxième utilisateur, j'ai ouvert **Active Directory Users and Computers**.  
J'ai sélectionné mon domaine **yboost.local**, puis **Users**. J'ai créé un nouvel utilisateur.

Après la création, l'utilisateur est apparu dans la liste des utilisateurs du domaine.

### Commande PowerShell pour créer un utilisateur
Voici la commande PowerShell pour créer un utilisateur :

```powershell
New-ADUser -Name "User 3" `
           -DisplayName "User 3" `
           -GivenName "User" `
           -Surname "3" `
           -SamAccountName "User3" `
           -UserPrincipalName "User3@yboost.local" `
           -EmailAddress "User3@yboost.local" `
           -Path "OU=Personnel,DC=IT-CONNECT,DC=LOCAL" `
           -AccountPassword(Read-Host -AsSecureString "123456789") `
           -Enabled $true
```
## Ajouter le PC au domaine

Pour ajouter le PC au domaine, j'ai ouvert Système dans le Panneau de configuration.

Puis, dans Paramètres système avancés, j'ai cliqué sur Nom de l'ordinateur et Modifier.
J'ai ajouté yboost.local comme domaine et redémarré la machine virtuelle. Le PC était maintenant ajouté au domaine.

## Désactiver le compte par défaut créé lors du setup
Pour désactiver l'utilisateur adam, j'ai ouvert Active Directory Users and Computers, sélectionné adam, puis cliqué sur Désactiver le compte.

### Sinon, j'aurais pu utiliser cette commande PowerShell :
```
Disable-ADAccount -Identity "adam"
```
## Rendu de la GPO
J'ai créé la GPO dans la Group Policy Management Console (GPMC).
J'ai configuré la GPO pour empêcher la désactivation de Windows Defender.
J'ai désactivé les options de désactivation de Defender et l'ai configuré pour rester activé.

Pour appliquer la GPO sur mon PC User, j'ai exécuté cette commande en tant qu'administrateur :

bash
Copier le code
gpupdate /force
Pour vérifier, j'ai utilisé cette commande :
```
gpresult /r
```
Enfsuite, j'ai testé sur mon PC User. Je ne pouvais pas désactiver Windows Defender.