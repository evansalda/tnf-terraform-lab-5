# STRUCTURER SON CODE

A ce stade, votre répertoire de travail devrait contenir les fichiers suivants :

```
répertoire-de-travail
|
main.tf
developpement.tfvars
```

L’ensemble de vos ressources sont déclarées dans le fichier **main.tf** dont le nombre de ligne commence à devenir inconfortable à parcourir.

Lorsque les commandes **init**, **plan** et **apply** sont exécutées, terraform recherche tous les fichiers .tf du répertoire courant et analyse leur contenu afin de s’initialiser, générer un plan d’exécution ou créer les ressources qui y sont déclarées : Le nom des fichiers et leur nombre n’a donc aucune importance.

## Création des fichiers .tf

Afin d’améliorer la lisibilité et la maintenabilité de votre code terraform, vous allez classer vos ressources dans des fichiers .tf distincts, en respectant une logique qui rendra votre développement plus confortable :
- Créez le fichier **backend.tf** et copiez-y la déclaration de votre **backend**
- Créez le fichier **provider.tf** et copiez-y la déclaration du **provider aws**
- Créez le fichier **variables.tf** et copiez-y la déclaration de vos 6 variables globales
- Créez le fichier **locals.tf** et copiez-y la déclaration de vos 3 variables locales
- Créez le fichier **security_groups.tf** et copiez-y la déclaration de vos **3 security groups**
- Supprimez le fichier **main.tf**

## Exécution du code terraform

Exécutez la commande **terraform fmt** puis la commande **terraform plan -var-file="developpement.tfvars"** : vous devriez obtenir le message **No changes. Infrastructure is up-to-date.**.

En effet, bien que vous ayez ajouté des fichiers, les ressources déclarées et la valeur de leurs paramètres n’ont pas changé : terraform n’a donc aucune action à effectuer.

Vous pouvez si vous le souhaitez exécuter le commande **terraform apply -auto-approve -var-file="developpement.tfvars"** pour confirmer que terraform n’effectue aucune action.