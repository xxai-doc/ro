<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

O parte a codului site-ului este open source, binevenit pentru a ajuta la optimizarea traducerii.

## codul front-end

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
