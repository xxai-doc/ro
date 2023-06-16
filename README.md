<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Este recomandat să instalați mai întâi nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) și apoi `direnv allow` după intrarea în director ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) va fi executat automat după intrarea în director).

Semnificația este: traducere chineză în japoneză, coreeană, engleză, traducere engleză în toate celelalte limbi. Dacă doriți să susțineți doar chineza și engleza, puteți scrie doar `zh: en` .

Semnificația este: traducere chineză în japoneză, coreeană, engleză, traducere engleză în toate celelalte limbi. Dacă doriți să susțineți doar chineza și engleza, puteți scrie doar `zh: en` .

* [codul front-end](https://github.com/xxai-art/web)
* [Pachete lingvistice pentru site-ul ca întreg](https://github.com/xxai-art/web/tree/main/i18n)
* [Pachete de limbi pentru modulele de conectare](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Documentație multilingvă a site-ului web](https://github.com/xxai-doc)

Limbajul de programare front-end este [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , care adaugă unele caracteristici bazate pe sintaxa coffeescript, vezi [./coffee_plus.md](./coffee_plus.md) .

## Internaționalizarea site-urilor web și a documentelor

Construiți-vă pe următoarele 3 proiecte

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Sufixul este `.mdt` , puteți utiliza o sintaxă similară cu `<+ ./coffee_plus/import.js>` pentru a face referire la fișiere externe și puteți genera reduceri cu sufixul `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  Traducerea Markdown nu va traduce coduri și link-uri și va stoca în cache propozițiile traduse. Dacă traducerea este modificată, dar textul original nu este modificat, executarea acesteia din nou nu va suprascrie modificarea traducerii.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Fișiere de limbă pentru traducerea site-urilor web generate `yaml` .

### Instrucțiuni de automatizare a traducerii documentelor

Vedeți depozitul de coduri [xxai-art/doc](https://github.com/xxai-art/doc)

Este recomandat să instalați mai întâi nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) și apoi `direnv allow` după intrarea în director ( [.envrc](https://github.com/xxai-art/doc/blob/main/.envrc) va fi executat automat după intrarea în director).

Pentru a evita baza mare de cod tradusă în sute de limbi, am creat o bază de cod separată pentru fiecare limbă și am creat o organizație pentru a stoca baza de cod.

Setarea variabilei de mediu `GITHUB_ACCESS_TOKEN` și apoi rularea [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) va crea automat depozitul de cod.

Desigur, îl puteți pune și într-o bază de cod.

Referința la scriptul de traducere [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

Codul de script este interpretat după cum urmează:

[bunx](https://bun.sh/docs/cli/bunx) este un înlocuitor pentru npx, care este mai rapid. Desigur, dacă nu aveți bun instalat, puteți utiliza `npx` în schimb.

`bunx mdt zh` redă `.mdt` în directorul zh ca `.md` , vezi cele 2 fișiere legate de mai jos

* [cafea_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [cafea_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` este codul de bază pentru traducere (dacă aveți instalat doar `nodejs` , dar `bun` și `direnv` nu sunt instalate, puteți rula și `npx i18n` pentru a traduce).

Acesta va analiza [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , configurația `i18n.yml` din acest document este după cum urmează:

```
en:
zh: ja ko en
```

Semnificația este: traducere chineză în japoneză, coreeană, engleză, traducere engleză în toate celelalte limbi. Dacă doriți să susțineți doar chineza și engleza, puteți scrie doar `zh: en` .

Ultimul este [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , care extrage conținutul dintre titlul principal și primul subtitlu al fiecărei limbi `README.md` pentru a genera o intrare `README.md` . Codul este foarte simplu, îl puteți privi singur.

Google API este folosit pentru traducerea gratuită. Dacă nu puteți accesa Google, vă rugăm să configurați și să setați un proxy, cum ar fi:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

Scriptul de traducere va genera un cache tradus în directorul `.i18n` , vă rugăm să îl verificați cu `git status` și să îl adăugați în depozitul de cod pentru a evita traducerile repetate.

Rulați `bunx i18n` de fiecare dată când modificați traducerea pentru a actualiza memoria cache.

Dacă textul original și traducerea sunt modificate în același timp, memoria cache va fi confuză, așa că dacă doriți să modificați, puteți modifica doar una, apoi rulați `bunx i18n` pentru a actualiza memoria cache.
