[VosFactures.fr](http://vosfactures.fr/) - Logiciel de facturation en ligne
===========

Format (template) des factures
---------------

En utilisant notre logiciel de facturation, vous avez accès à un certain nombre de formats de factures. Si l'un d'eux ne répond pas à vos attentes, vous pouvez créer votre propre modèle. Il vous suffit de vous connecter à votre compte (si vous n'êtes pas encore inscrit, [vous pouvez ouvrir un compte gratuitement] (https://app.vosfactures.fr/signup) ) et de cliquer sur Paramètres > Paramètres du compte > Formats d'impression. Cliquez sur le bouton "Ajouter un nouveau format".



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
{{place}} - miejsce wystawienia
{{street}} - numéro et nom de rue
{{tax_no}} - numéro de taxe
{{country}} - pays
{{www}} 
{{email}}
{{fax}}
{{phone}}
{{bank}} - domciliation bancaire
{{person}}
{{bank_account}} - numéro de compte
{{buyer}} - nom de l'acheteur
{{buyer_post_code}} - code postal de l'acheteur
{{buyer_place}}
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
{{all_in_words}} 
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

{{#each positions}}  - ligne des tableaux 
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
  {{tax}} - taux de tax
  {{tax_value}} - montant de tax
{{/each}}

{{#each summary}} : 
  {{total_price_net}}
  {{total_price_gross}}
  {{tax}}
  {{tax_value}} 
{{/each}}

{{footer}}
```




Szablony e-maili
---------------
Można tworzyć szablony e-maili które będą wysyłane do klientów. Są 2 szablony dla standardowego wysyłania faktury oraz
do wysyłania przypomnień o niezapłaconych fakturyach. Tworząc szablony używa się tych samych zmiennych co przy szablonach 
faktrur i korzysta się także z [Handlebars](http://handlebarsjs.com/).

Domyślne szablon wysyłania faktur:
```shell
Dzień dobry,

dziękujemy za skorzystanie z naszych usług. 
Załączam dokument {{document_type}} {{number}} na kwotę {{total_price_gross}} brutto.

Link do podglądu {{view_url}}


{{footer}}
```

Domyślne szablon przypomnienia o niezapłaconej fakturze:
```shell
Dzień dobry,

przypominamy o zaległej płatności za {{document_type}} {{number}} na kwotę {{total_price_gross}} brutto.

Link do podglądu: {{view_url}}

{{footer}}
```


Funkcje dostępne w szablonach faktur i e-maili
---------------

w szablonach dostepne są następujące funkcje:

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

Przykład wywołania funkcji:

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
  info dla danego departamento
{{else}}
  info dla innych departamentow
{{/eq}}


{{#for size_from size_to}}
    no: {{no}}
{{/for}}
```


Import danych
---------------

Możliwy jest import danych z dowolnych programów które zapiszą dane do plików  .TXT, .CSV, .XLS, .ODS, .XLSX, .TSV, .XML
Podczas importu samodzienie można ustawiać jakie kolumny i wiersze są importowane.

Można importować Faktury, Klientów, Produkty

Dodatkowo dostępne są opcje importu: Sprzedaż na ALLEGRO.PL (XML), Zakupy w ACTION S.A. (CSV), Zakupy w ABC DATA S.A. (XML), Faktury, klienci i produkty z CDN optima 


API
---------------

Opis API znajduje się tu: [Fakturownia API](https://github.com/radgost/fakturownia-api)

