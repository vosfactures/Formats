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
{{buyer_person}} - imię i nazwisko odbiorcy
{{buyer_company}} - nom de la compagnie de l'acheteur
{{total_price_net}} - total net (HT)
{{total_price_net_with_currency}} - total net (HT) avec devise
{{total_price_gross}} - total brut (TTC) 
{{total_price_gross_with_currency}} - total brut (TTC) avec devise
{{tax_value}} - montant de la taxe
{{tax_value_with_currency}} - montant de la taxe avec devise
{{notes}} - informations spécifiques
{{outstanding}} - montant à payer (en chiffres)
{{outstanding_in_words}} - montant à payer (en lettres)
{{all_in_words}} 
{{payment_to}} - termin płatności
{{type_of_payment}} - Moyen de paiement
{{paid}} - montant payé
{{logo_url}}
{{stamp_url}}
{{token}}
{{oid}} - nr zamówienia
{{description_long}} - dodatkowe uwagi (drukowane na drugiej stronie)
{{description_footer}} - dodatkowe uwagi (drukowane na dole strony)
{{view_url}}
{{payment_url}}
{{tax_name}}
{{currency}} - waluta
{{currency_symbol}}
{{currency_short}}
{{exchange_currency}} - przeliczanie na walutę
{{use_delivery_address}} - inny adres korespondencyjny
{{delivery_address}} - adresat
{{lang}} - język
{{discount}} - rabat
{{show_discount}}
{{income}} - przychód
{{exchange_rate}} - kurs
{{total_price_net_in_main_currency}}
{{total_price_gross_in_main_currency}}
{{additional_info}}
{{department}} - dział / oddział firmy - dostępne są pola id, name, kind ... np {{department.id}} {{department.name}}

{{#each positions}} : 
  {{no}}
  {{item}} - nazwa produktu/usługi
  {{additional_info}} - dodatkowe pole na pozycjach faktury
  {{discount}}
  {{quantity}} - ilość
  {{unit_price_net}}
  {{unit_price_net_with_discount}}
  {{unit_price_gross}}
  {{total_price_net}} - wartość netto
  {{total_price_gross}} - wartość brutto
  {{tax}} - stawka vat
  {{tax_value}} - wartość vat 
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

