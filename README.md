# txt2WebGame-dev-parser
Early version of 'Lite YAML' parser to HTML. LANG=PL

Od roku zastanawiam się nad generatorem gier przeglądarkowych w stylu Vallheru. 
txt2WebGame to projekt, którego celem jest opracowanie nowego formatu wymiany 
danych tekstowych, tak by za pomocą prostych poleceń móc stworzyć całą stronę 
internetową.

Początkowo spodobały mi się formaty YAML oraz Python Kivy Kv. Problem w tym że 
YAML jest strasznie wolny. Dlatego powstał pomysł czegoś co nazywam 'Lite YAMLem'. 
Ciągi znaków zapisujemy jak w każdym pliku YAML jako: 
```
key: value

key:
  value
  
key:
value

key:
      value
```
Przy czym rekomendowana jest wersja numer 2, z dwiema spacjami. Co z resztą specyfikacji ? 
Nie ma. Plik szablonów jest więc jakby niepełnym plikiem YAML. 

Jakby nie patrzeć podstawowym celem generatora będzie tworzenie ciągów znaków, które zostaną 
wklejone do sekcji head, body lub footer. Drugim celem będzie generowanie funkcji Fetch, 
wysyłających zapytania AJAX do serwera. 

"slash" - Creates hashes like #/ and #/sunshine/lollipops
    "noslash" - Creates hashes like # and #sunshine/lollipops
    "hashbang" - Creates “ajax crawlable” (deprecated by Google) hashes like #!/ and #!/sunshine/lollipops
https://reactrouter.com/web/api/HashRouter

## Development

Zamień wiele mniejszych plików w jeden duży
```npx webpack ./index.mjs -o bundle/main.js```

Serwer
```npx http-server```
