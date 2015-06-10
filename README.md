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
{{sell_date_kind}} - 
{{company}} - nom de la compagnie/département
{{person}} - nom du vendeur
{{post_code}} - code postal
{{place}} - ville
{{street}} - numéro et nom de rue
{{tax_no}} - numéro de taxe
{{country}} - pays
{{address}} -
{{www}} - adresse internet
{{email}} - adresse email
{{fax}} - numéro de fax
{{phone}} - numéro de téléphone
{{bank}} - domiciliation bancaire et numéro
{{bank_account}} - numéro de compte bancaire (RIB ou IBAN)
{{department.bank_swift}} - numéro BIC 
{{department.bank_name}} - domiciliation bancaire
{{buyer}} - nom de l'acheteur
{{buyer_post_code}} - code postal de l'acheteur
{{buyer_place}} - ville de l'acheteur
{{buyer_street}} - numéro et nom de rue de l'acheteur
{{buyer_country}} - pays de l'acheteur
{{buyer_tax_no}} - numéro de taxe de l'acheteur
{{buyer_person}} - nom (et prénom) de l'acheteur
{{buyer_company}} - nom de la compagnie de l'acheteur
{{use_delivery_address}} - afficher l'adresse de livraison
{{delivery_address}} - adresse de livraison
{{buyer_note}} - description additionnelle
{{show_buyer_note}} - afficher la description additionnelle
{{total_price_net}} - total HT
{{total_price_net_with_currency}} - total HT avec devise
{{total_price_gross}} - total TTC 
{{total_price_gross_with_currency}} - total TTC avec devise
{{tax_value}} - montant de la taxe
{{tax_value_with_currency}} - montant de la taxe avec devise
{{notes}} - informations spécifiques
{{outstanding}} - montant à payer (en chiffres)
{{outstanding_in_exchange_currency}} - montant converti à payer (en chiffres)
{{outstanding_in_words}} - montant à payer (en lettres)
{{outstanding_in_words_in_exchange_currency}} - montant converti à payer (en lettres)
{{negative_outstanding}} - solde en votre faveur (en chiffres)
{{absolute_outstanding}}
{{absolute_outstanding_in_words}}
{{all_in_words_in_exchange_currency}}
{{all_in_words}} - montant total TTC (en lettres)
{{payment_to}} - date limite de règlement
{{type_of_payment}} - Mode de règlement
{{paid}} - montant payé
{{logo_url}} - logo
{{stamp_url}} - tampon
{{stamp_below_sign_url}}
{{status_paid}} - 
{{token}} - code
{{oid}} - numéro de commande
{{description_long}} - texte additionnel (imprimé sur la page suivante)
{{description_footer}} - Bas de page
{{view_url}}
{{view_link}}
{{payment_url}}
{{payment_button_url}}
{{tax_name}} - nom de la taxe
{{tax2_name}} - nom de la deuxième taxe
{{tax_value_name}} -
{{currency}} - devise
{{currency_symbol}} - devise (symbole)
{{currency_short}} - devise (abrégé)
{{exchange_currency}} - convertir en
{{lang}} - langue
{{discount}} - réduction
{{show_discount}} - afficher réduction
{{income}} - revenu
{{exchange_rate}} - taux de change
{{exchange_note}} - note sur le taux
{{exchange_date}} - date de la conversion
{{exchange_currency}} - devise (conversion)
{{exchange_currency_rate}} - 
{{total_price_net_in_main_currency}} - total HT avec devise principale
{{total_price_gross_in_main_currency}} - total TTC avec devise principale
{{total_price_net_in_exchange_currency}} - total HT avec devise de conversion
{{total_price_gross_in_exchange_currency}} - total TTC avec devise de conversion
{{tax_value_in_exchange_currency}} - montant de taxe avec devise de conversion
{{additional_info}} - colonne additionnelle
{{additional_fields}} - champ additionnel 
{{additional_field_name}} - 
{{additional_field_value}} - 
{{department}} - département/compagnie - les champs sont id, nom, type ... par ex: {{department.id}} {{department.name}}
{{client}}
{{client_panel_view_url}} - url de l'accès client
{{client_panel_view_link}}
{{additional_info_desc}} - Titre de la colonne additionnelle
{{use_product_code}} - afficher la colonne Référence
{{tax_visible}} - afficher colonne taxe
{{tax2_visible}} - afficher deuxième colonne taxe
{{long_exchange_note}} - taux de change appliqué
{{positions_total_price_net}}
{{positions_total_price_gross}}
{{positons_total_tax}}
{{correction}}
{{corrected_content_before}}
{{corrected_content_after}}
{{seller_tax_no_kind}} - Numéro d'identification du vendeur
{{buyer_tax_no_kind}} - Numéro d'identification de l'acheteur
{{show_totals}} - afficher un résumé du total net, brut et de la TVA
{{hide_tax}} - afficher les montants TTC uniquement 
{{show_tax_split}} - afficher le résumé des différents taux de taxe
{{show_paid_date}} - afficher la date de paiement
{{paid_date}} - date de paiement
{{show_date_and_sign}} - afficher la mention " Date et signature du client..."
{{show_product_description}} - afficher la description des produits
{{paid_mark_url}}
{{sales_code}}
{{show_unit_price_gross}} - afficher le prix unitaire TTC
{{total_discount}} - réduction globale
{{transaction_id}} - ID de la transaction
{{show_paid_logo}} - afficher le tampon "Payé"
{{client_external_id}} - Réf/code client
{{locale}}
{{final}} - facture de solde
{{advanced}}
{{advanced_num}}
{{total_tax_inscription}}

{{#each positions}}  - ligne des tableaux :
  {{no}} - numéro de ligne
  {{code}} - référence du produit
  {{item}} - nom du produit
  {{description}} - description du produit
  {{additional_info}} - champ additionnel 
  {{discount}} - réduction
  {{quantity}} - quantité
  {{unit_price_net}} - prix unitaire ht
  {{unit_price_net_with_discount}} - prix unitaire ht après réduction
  {{unit_price_gross_with_discount}} - prix unitaire ttc après réduction
  {{unit_price_gross}} - prix unitaire ttc
  {{total_price_net}} - total HT
  {{total_price_gross}} - total ttc
  {{tax}} - taux de taxe
  {{tax2}} - taux de la deuxième taxe
  {{tax_value}} - montant de taxe
  {{kind}}
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

Description de l'[API de VosFactures](https://github.com/vosfactures/API) 

