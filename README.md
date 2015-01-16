[VosFactures.fr](http://vosfactures.fr/) - Logiciel de facturation en ligne
===========

Format (template) des factures
---------------

En utilisant notre logiciel de facturation, vous avez accès à un certain nombre de formats de factures. Si l'un d'eux ne répond pas à vos attentes, vous pouvez créer votre propre modèle. Il vous suffit de vous connecter à votre compte (si vous n'êtes pas encore inscrit, [vous pouvez ouvrir un compte gratuitement] (https://app.vosfactures.fr/signup) ), de cliquer sur Paramètres > Paramètres du compte > Formats d'impression puis de cliquer sur le bouton "Ajouter un nouveau format".



Quelques exemples de formats de factures:

HTML: https://github.com/fakturownia/szablony/blob/master/default.hbs.html

CSS: https://github.com/fakturownia/szablony/blob/master/default.css

Les modèles sont créés en HTML et CSS en utilisant [Handlebars](http://handlebarsjs.com/)

Les variables qui peuvent être utilisées dans les formats sont:
 
```shell
{{document_type}} type de document
{{kind}} - type
{{number}} - numéro
{{title}} - titre
{{issue_date}} - date de création
{{issue_place}} - lieu de création
{{print_option}} 
{{sell_date}} - data de vente
{{company}} - nom de la compagnie/département
{{post_code}} - code postal
{{place}} - ville
{{street}} - numéro et nom de rue
{{tax_no}} - numéro de taxe
{{country}} - pays
{{www}} - adresse internet
{{email}} - adresse email
{{fax}} - numéro de fax
{{phone}} - numéro de téléphone
{{bank}} - domciliation bancaire
{{person}} - nom du vendeur
{{bank_account}} - numéro de compte
{{buyer}} - nom de l'acheteur
{{buyer_post_code}} - code postal de l'acheteur
{{buyer_place}} - ville de l'acheteur
{{buyer_street}} - numéro et nom de rue de l'acheteur
{{buyer_country}} - pays de l'acheteur
{{buyer_tax_no}} - numéro de tax de l'acheteur
{{buyer_person}} - nom (et prénom) de l'acheteur
{{buyer_company}} - nom de la compagnie de l'acheteur
{{total_price_net}} - total HT
{{total_price_net_with_currency}} - total HT avec devise
{{total_price_gross}} - total TTC 
{{total_price_gross_with_currency}} - total TTC avec devise
{{tax_value}} - montant de la taxe
{{tax_value_with_currency}} - montant de la taxe avec devise
{{notes}} - informations spécifiques
{{outstanding}} - montant à payer (en chiffres)
{{outstanding_in_words}} - montant à payer (en lettres)
{{all_in_words}} - montant total TTC (en lettres)
{{payment_to}} - date limite de règlement
{{type_of_payment}} - Mode de règlement
{{paid}} - montant payé
{{logo_url}} - logo
{{stamp_url}} - tampon
{{token}} - code
{{oid}} - numéro de commande
{{description_long}} - texte additionnel (imprimé sur la page suivante)
{{description_footer}} - Bas de page
{{view_url}}
{{payment_url}}
{{tax_name}} - nom de la taxe
{{currency}} - devise
{{currency_symbol}} - devise (symbole)
{{currency_short}} - devise (abrégé)
{{exchange_currency}} - convertir en
{{use_delivery_address}} - afficher l'adresse de livraison
{{delivery_address}} - adresse de livraison
{{lang}} - langue
{{discount}} - réduction
{{show_discount}} - afficher réduction
{{income}} - revenu
{{exchange_rate}} - taux de change
{{total_price_net_in_main_currency}} - total HT avec devise principale
{{total_price_gross_in_main_currency}} - total TTC avec devise principale
{{additional_info}} - champ additionnel
{{department}} - département/compagnie - les champs sont id, nom, type ... par ex: {{department.id}} {{department.name}}

{{#each positions}}  - ligne des tableaux :
  {{no}} - numéro de ligne
  {{item}} - nom du produit
  {{additional_info}} - champ additionnel 
  {{discount}} - réduction
  {{quantity}} - quantité
  {{unit_price_net}} - prix unitaire ht
  {{unit_price_net_with_discount}} - prix unitaire ht après réduction
  {{unit_price_gross}} - prix unitaire ttc
  {{total_price_net}} - total HT
  {{total_price_gross}} - total ttc
  {{tax}} - taux de taxe
  {{tax_value}} - montant de taxe
{{/each}}

{{#each summary}} - résumé des totaux :
  {{total_price_net}} - total HT
  {{total_price_gross}} - total TTC
  {{tax}} - taux de taxe
  {{tax_value}} - total taxe
{{/each}}

{{footer}} - bas de page
```




Format des emails
---------------
Le système propose par défaut un contenu pour l'envoi des documents de facturation, et un contenu pour l'envoi de relances en cas de factures impayées. Vous pouvez personnaliser le contenu des e-mails envoyés aux clients. Le texte des emails utilisent les mêmes variables que les formats (voir ci-dessus) et utilise aussi [Handlebars](http://handlebarsjs.com/).

Contenu par défaut de l'email accompagnant l'envoi des factures:
```shell
Bonjour,

Veuillez trouver le document suivant: {{document_type}} numéro {{number}} d’un montant total de {{total_price_gross_with_currency}}.
Vous pouvez visualiser le document en cliquant sur le lien: {{{view_link}}}

{{footer}}

```

Contenu par défaut de l'email de relance en cas de factures impayées:
```shell
Bonjour,

Veuillez trouver la {{document_type}} numéro {{number}} d’un montant de {{total_price_gross_with_currency}} qui reste à ce jour impayée.

Vous pouvez visualiser la facture en cliquant sur le lien suivant: {{{view_link}}}

Dans l’attente de votre prompt règlement,

Bien cordialement,

{{footer}}
```


Fonctions disponibles dans les formats de factures et des e-mails
---------------

Les formats peuvent inclure les fonctions suivantes:

```shell
  if
  for
  eq 
  not_eq
  lt
  gt
  tt
  include
  include_in_col
  in 
  not_in
```

Exemple:

```shell  
{{#if val1 }}
  ok
{{else}}
  not ok
}}

{{#lt val1 17 }}
  <17
}}

{{#mt val1 17 }}
  >17
{{else}}
 <17
}}

{{#eq department_id "123"}}
  info sur le département
{{else}}
  info sur les autres départements
{{/eq}}


{{#for size_from size_to}}
    numéro: {{no}}
{{/for}}
```


Importation de données
---------------

Il vous est possible d'importer dans votre compte VosFactures des données existantes depuis n'importe quel programme si celles-ci sont dans un fichier .TXT, .CSV, .XLS, .ods, XLSX, .tsv, .xml bure. L'importation de fichier se fait depuis l'onglet Paramètres > Importation. Vous pouvez importer des factures (et autres documents de facturation), des clients et fournisseurs, vos catalogues produits, et des relevés bancaires. Durant l'importation, vous pouvez choisir quelles colonnes et lignes à importer. 




API
---------------

Description de l'[API de VosFactures](https://app.vosfactures.fr/api) 

