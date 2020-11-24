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

## Założenia

Można znacząco zwiększyć wydajność, używając statycznych plików HTML. 
Ograniczy to połączenia z serwerem i zwiększy liczbę graczy online bez alarmowania
administratora hostingu. 

Taki plik HTML będzie się składał z kilku powtarzających się elementów:
- Długi tekst
- Krótki tekst
- Obraz
- Połączenie Fetch (operacje na bazie danych)
- Odpowiedzi serwera (np. lista graczy online)

Parser pozwoli na zapisanie takiej treści w formie 
zrozumiałej dla człowieka. Opcjonalnie będzie możliwość 
zakodowania plików w formacie binarnym.

Wersja developerska pozwala na podgląd szablonu, po zamianie na plik HTML. 
Żeby nie marnować już czasu, wszystkie strony są przekształcane pojedynczo i 
zapisywane jako hash-e. Obsługiwane są wszystkie 3 wersje:

- "slash" - Creates hashes like #/ and #/sunshine/lollipops
- "noslash" - Creates hashes like # and #sunshine/lollipops
- "hashbang" - Creates “ajax crawlable” (deprecated by Google) hashes like #!/ and #!/sunshine/lollipops
```https://reactrouter.com/web/api/HashRouter```

Idzie to mniej więcej tak:
- Wysyłam szablon
- Otrzymuję ciąg znaków w LocalStorage
- Po wybraniu strony, jej zawartość jest podmieniana na tą z LocalStorage
- Jeśli dołączono zapytanie Fetch, łączę się z serwerem

Na chwilę obecną muszę jeszcze stworzyć generator miast (tablic).

Wersję pełną mam zapisaną w Rubinie. Najprawdopodobniej będzie oparta 
o format binarny MessagePack. Będzie odpowiadać nie tylko za generowanie 
plików HTML, CSS, JS ale też za tworzenie plików SQL do szybkiego stworzenia 
bazy danych. Na chwilę obecną jest to SQLite3 ale myślę też nad MySQL dump. 

Ogółem automatyczny generator ma pomóc w stworzeniu niezależnych od serwera i 
bazy danych przeglądarkowych gier tekstowych. Jak się uda to powstaną automatyczne 
instalatory zdejmujące obowiązek szukania hostingu i wgrywania na niego plików. 

## Development

Zamień wiele mniejszych plików w jeden duży
```npx webpack ./index.mjs -o bundle/main.js```

Serwer
```npx http-server```
