[VosFactures.fr](http://vosfactures.fr/) - Logiciel de facturation en ligne
===========

Formats (templates) des factures
---------------

## Principe
En utilisant notre logiciel de facturation, vous avez accès à un certain nombre de formats de factures (mises en page). </br>
Si l'un d'eux ne répond pas à vos attentes, <b>vous pouvez créer votre propre modèle</b>.</br> 
Il vous suffit de vous connecter à votre compte (si vous n'êtes pas encore inscrit : https://app.vosfactures.fr/signup pour un essai gratuit), de cliquer sur Paramètres > Paramètres du compte > Formats d'impression, puis de cliquer sur le bouton "Ajouter un nouveau format". Vous pouvez choisir le format par défaut que vous souhaitez modifier, comme expliqué ici: https://aide.vosfactures.fr/8631976-Cr-er-un-format-personnalis-

## Documentation 

Vous trouverez sur Github la documentation de chacun des formats par défaut, c'est-à-dire la partie HTML et la partie CSS de chaque format. Les formats sont créés en HTML et CSS en utilisant [Handlebars](https://handlebarsjs.com/)

Les formats utilisent des fichiers partiels, représentés dans le code HTML par un tag {{>fichier_partiel}}. Ces fichiers partiels sont accessibles ici: https://github.com/vosfactures/Formats/tree/master/partials.


## Variables handlebars

Vous pouvez visualiser les données d'une facture en handlebars en ajoutant le suffixe <b>.handlebars</b> à l'url (ex: moncompte.vosfactures.fr/invoices/232342321.handlebars). <br/>
Les principales variables qui peuvent être utilisées dans les formats sont:
 
```shell
{{document_type}} type de document
{{kind}} - type ("vat" pour facture, "estimate" pour devis, "proforma" pour facture proforma, "correction" pour avoir, "client_order" pour bon de commande de client, "advance" pour facture d'acompte", "final" pour facture de solde, "invoice_other" pour autre type de document)
{{number}} - numéro
{{title}} - titre
{{issue_date}} - date de création
{{issue_place}} - lieu de création
{{print_option}} 
{{place}} - lieu de vente
{{sell_date}} - date additionnelle
{{sell_date_kind}} - intitulé de la date additionnelle
{{today_date}} - date du jour
{{invoice_category}} - catégorie du document
{{company}} - nom de la compagnie/département
{{person}} - nom du vendeur
{{post_code}} - code postal du vendeur
{{street}} - numéro et nom de rue du vendeur
{{tax_no}} - numéro de taxe du vendeur
{{country}} - pays du vendeur
{{address}} - adresse complète du vendeur
{{www}} - adresse internet du vendeur
{{email}} - adresse email du vendeur
{{fax}} - numéro de fax du vendeur
{{phone}} - numéro de téléphone du vendeur
{{bank}} - domiciliation bancaire et numéro de compte du vendeur
{{bank_account}} - numéro de compte bancaire (RIB ou IBAN) du vendeur
{{department.bank_swift}} - numéro BIC du vendeur
{{department.bank_name}} - domiciliation bancaire du vendeur
{{buyer}} - nom de l'acheteur
{{buyer_post_code}} - code postal de l'acheteur
{{buyer_place}} - ville de l'acheteur
{{buyer_street}} - numéro et nom de rue de l'acheteur
{{buyer_country}} - pays de l'acheteur
{{buyer_tax_no}} - numéro de taxe de l'acheteur
{{buyer_person}} - nom (et prénom) de l'acheteur
{{buyer_company}} - nom de la compagnie de l'acheteur
{buyer_phone}} - n° de tel de l'acheteur (correspond au champ "Téléphone" du contact)
{buyer_mobile_phone}} - n° de tel portable de l'acheteur (correspond au champ Tél. portable du contact)
{{seller_tax_no_kind}} - Numéro d'identification du vendeur
{{buyer_tax_no_kind}} - Numéro d'identification de l'acheteur
{{client.external_id}} - Réf/code client
{{use_delivery_address}} - afficher l'adresse de livraison
{{delivery_address}} - adresse de livraison
{{buyer_note}} - description additionnelle
{{show_buyer_note}} - afficher la description additionnelle
{{buyer_tax_no_kind}} - Numéro d'identification de l'acheteur
{{use_product_code}} - afficher la colonne Référence
{{additional_info}} - colonne additionnelle
{{additional_info_desc}} - Titre de la colonne additionnelle
{{discount}} - réduction (montant)
{{show_discount}} - afficher réduction
{{total_price_net}} - total HT
{{total_price_net_with_currency}} - total HT avec devise
{{total_price_gross}} - total TTC 
{{total_price_gross_with_currency}} - total TTC avec devise
{{tax_value}} - montant de la taxe
{{tax_value_with_currency}} - montant de la taxe avec devise
{{tax_name}} - nom de la taxe
{{tax2_name}} - nom de la deuxième taxe
{{tax_value_name}} - nom de la taxe 
{{tax_visible}} - afficher colonne taxe
{{tax2_visible}} - afficher deuxième colonne taxe
{{currency}} - devise
{{currency_symbol}} - devise (symbole)
{{currency_short}} - devise (abrégé)
{{exchange_currency}} - convertir en
{{lang}} - langue
{{exchange_currency_rate}} - taux de change (sur les documents)
{{exchange_note}} - note sur le taux
{{exchange_date}} - date de la conversion
{{exchange_currency}} - devise (conversion)
{{exchange_rate}} - taux de change (utilisé dans les rapports)
{{long_exchange_note}} - taux de change appliqué
{{total_price_net_in_main_currency}} - total HT avec devise principale
{{total_price_gross_in_main_currency}} - total TTC avec devise principale
{{total_price_net_in_exchange_currency}} - total HT avec devise de conversion
{{total_price_gross_in_exchange_currency}} - total TTC avec devise de conversion
{{tax_value_in_exchange_currency}} - montant de taxe avec devise de conversion
{{outstanding}} - montant à payer (en chiffres)
{{outstanding_in_exchange_currency}} - montant converti à payer (en chiffres)
{{outstanding_in_words}} - montant à payer (en lettres)
{{outstanding_in_words_in_exchange_currency}} - montant converti à payer (en lettres)
{{negative_outstanding}} - solde en votre faveur (en chiffres)
{{absolute_outstanding}} -  montant à payer en valeur absolue (en chiffres)
{{absolute_outstanding_in_words}} - montant à payer en valeur absolue (en lettres)
{{all_in_words_in_exchange_currency}} montant total converti (en lettres)
{{all_in_words}} - montant total (en lettres)
{{paid}} - montant payé
{{status_paid}} - Etat Payé ou non
{{oid}} - numéro de commande
{{payment_to}} - date limite de règlement
{{type_of_payment}} - Mode de règlement
{{notes}} - informations spécifiques
{{additional_field_name}} - titre du champ additionnel
{{additional_field_value}} - contenu du champ additionnel
{{logo_url}} - url du logo
{{stamp_url}} - url du tampon
{{stamp_below_sign_url}} - url du tampon sous le nom du vendeur
{{token}} - code
{{view_url}}
{{view_link}} - lien vers l'aperçu du document
{{payment_link}} - Lien vers Paiement en ligne (lien direct permettant au client de payer en ligne la facture)
{{payment_button_url}}
{{income}} - revenu
{{department}} - département/compagnie - les champs sont id, nom, type ... par ex: {{department.id}} {{department.name}}
{{client}} 
{{client_panel_view_url}} - Lien url de l'accès client
{{client_panel_view_link}} 
{{show_totals}} - afficher un résumé du total net, brut et de la TVA
{{hide_tax}} - afficher les montants TTC uniquement 
{{show_tax_split}} - afficher le résumé des différents taux de taxe
{{show_paid_date}} - afficher la date de paiement
{{paid_date}} - date de paiement
{{show_date_and_sign}} - afficher la mention " Date et signature du client..."
{{show_product_description}} - afficher la description des produits
{{show_unit_price_gross}} - afficher le prix unitaire TTC
{{total_discount}} - réduction globale (montant)
{{global_discount_percent}} - réduction globale (en %)
{{show_paid_logo}} - afficher le tampon "Payé"
{{paid_mark_url}} - url du tampon vert "Payé"
{{sales_code}}
{{transaction_id}} - ID de la transaction
{{locale}} - 
{{final}} - facture de solde
{{advanced}} - acompte
{{advanced_num}} - nombre des acomptes liés à une facture finale
{{description_long}} - texte additionnel (imprimé sur la page suivante)
{{description_footer}} - Bas de page

{{#each positions}}  - ligne des tableaux :
  {{no}} - numéro de ligne
  {{kind}} - type de ligne (ligne de produit ou ligne de texte)
  {{code}} - référence du produit
  {{item}} - nom du produit
  {{description}} - description du produit
  {{additional_info}} - champ additionnel 
  {{discount}} - réduction
  {{quantity}} - quantité
  {{positions_total_quantity}} - total des quantités
  {{unit_price_net}} - prix unitaire ht
  {{unit_price_gross}} - prix unitaire ttc
  {{unit_price_net_with_discount}} - prix unitaire ht après réduction
  {{unit_price_gross_with_discount}} - prix unitaire ttc après réduction
  {{positions_total_price_net}} - total HT de la ligne
  {{positions_total_price_gross}} - total TTC de la ligne
  {{positons_total_tax}} - total taxe de la ligne
  {{total_price_net}} - total ht
  {{total_price_gross}} - total ttc
  {{tax}} - taux de taxe
  {{tax2}} - taux de la deuxième taxe
  {{tax_value}} - montant de taxe
{{/each}}

{{#each summary}} - résumé des totaux :
  {{total_price_net}} - total HT
  {{total_price_gross}} - total TTC
  {{tax}} - taux de taxe
  {{tax_value}} - total taxe
  {{total_price_gross_without_discount}} - sous-total TTC avant réduction
  {{total_price_net_without_discount}} - sous-total HT avant réduction
  {{global_discount_net}} - montant total HT de la réduction
  {{global_discount_gross}} - montant total TTC de la réduction
{{/each}}

{{footer}} - bas de page
```




Format des emails
---------------
Le système propose par défaut un contenu pour l'envoi des documents de facturation, et un contenu pour l'envoi de relances en cas de factures impayées. Vous pouvez personnaliser le contenu des e-mails envoyés aux clients. Le texte des emails utilisent les mêmes variables que les formats (voir ci-dessus) et utilise aussi [Handlebars](http://handlebarsjs.com/).

Contenu par défaut de l'email accompagnant l'envoi des factures:
```shell
Bonjour, 

Veuillez trouver en pièce jointe le document suivant: 
{{document_type}} numéro {{number}} d’un montant total de {{total_price_gross_with_currency}}. 

Vous pouvez également visualiser le document en cliquant sur le lien suivant: {{{view_link}}}  

{{footer}}
```

Contenu par défaut de l'email de relance en cas de factures impayées:
```shell
Bonjour, 

Veuillez trouver en pièce jointe la {{document_type}} numéro {{number}} d’un montant de {{outstanding}} qui {{#if overdue}}reste à ce jour impayé.{{else}}arrive à échéance le {{payment_to}}.{{/if}}

Vous pouvez visualiser la {{document_type}} en cliquant sur le lien suivant: {{{view_link}}}

Dans l’attente de votre prompt règlement,

Bien cordialement,

{{footer}}
```

Vous pouvez également utiliser les variables suivantes pour vos emails de relance: 
```shell
{{inc reminder_no}} - numéro de la relance que vous envoyez, ie. N
{{reminder_no}} - nombre de relances jusque là envoyées, ie. N-1 par rapport à la relance que vous allez envoyer
{{dec reminder_no}} - nombre de relances jusque là envoyées, ie. N-2 par rapport à la relance que vous allez envoyer
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

Il vous est possible d'importer dans votre compte VosFactures des données existantes depuis n'importe quel programme si celles-ci sont dans un fichier .TXT, .CSV, .XLS, .ods, XLSX, .tsv, .xml bure. L'importation de fichier se fait depuis l'onglet Paramètres > Importation. Vous pouvez importer des factures d'achat et de vente (et autres documents de facturation), des clients et fournisseurs, vos catalogues produits, et des relevés bancaires. Durant l'importation, vous pouvez choisir quelles colonnes et lignes importer. 




API
---------------

Lien vers la documentation de l'[API de VosFactures](https://github.com/vosfactures/API) 

