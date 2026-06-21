# EduReçu — Gestion Paiements Scolaires

Application web de gestion des paiements scolaires avec génération de reçus PDF et alertes.

## Déploiement sur Netlify

### Méthode 1 — Glisser-déposer (la plus simple)
1. Allez sur **https://app.netlify.com**
2. Connectez-vous (ou créez un compte gratuit)
3. Sur le tableau de bord, faites **glisser-déposer le dossier entier** dans la zone de déploiement
4. Netlify génère automatiquement une URL (ex: `https://ecole-recus.netlify.app`)

### Méthode 2 — Via GitHub
1. Créez un dépôt GitHub et uploadez ces fichiers
2. Sur Netlify → **Add new site → Import an existing project**
3. Connectez votre dépôt GitHub
4. Build command : *(laisser vide)*
5. Publish directory : `.`
6. Cliquez **Deploy**

## Fichiers inclus

| Fichier | Rôle |
|---------|------|
| `index.html` | Application complète |
| `manifest.json` | Configuration PWA (installable sur mobile) |
| `netlify.toml` | Configuration Netlify (headers, redirects) |
| `_headers` | En-têtes de sécurité HTTP |
| `_redirects` | Redirection SPA |

## Domaine personnalisé

Dans Netlify → **Domain settings → Add custom domain** :
- Entrez votre domaine (ex: `paiements.ecole.ma`)
- Suivez les instructions DNS
- HTTPS activé automatiquement

## Configuration Firebase (synchronisation multi-appareils)

1. Créez un projet sur **console.firebase.google.com**
2. Créez une base Firestore en mode production
3. Réglez les règles Firestore :
```
rules_version = '2';
service cloud.firestore.default_database {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```
4. Dans l'application → **Paramètres → 🔥 Configuration Firebase**
5. Collez vos identifiants Firebase et cliquez **Connecter Firebase**

## Comptes par défaut

| Identifiant | Mot de passe | Rôle |
|-------------|-------------|------|
| `admin` | `admin123` | Administrateur (accès complet) |
| `utilisateur` | `user123` | Utilisateur (pas accès Paramètres) |

⚠️ **Changez les mots de passe après le premier déploiement !**
Test Vercel
