# GIT repository opschonen

Resultaat:
2 repo's waarvan 1 secrets/config bevat en de andere (publieke) code

### Benodigheden
- Python
- Git filter repo tool

Zie voor installatie en gebruik van het filter: https://github.com/ITforCare-GGD-Amsterdam/svn-to-git

## Repo met publieke code

- Kloon de bestaande repo:

    `git clone https://github.com/landrej/CleanGit.git public` 

- Maak een lijst van bestanden die je eruit wilt filteren

    `filter.txt`

- Een handige tool om op zoek te gaan naar bestanden om op te filteren is TortoiseGit

- Zet de bestanden in filter.txt
```
map met secrets/bestand met secrets.txt
mijn pincode.txt
```
- Schoon nu het filter op, verwijder de bestanden die in filter.txt staan.

    `git filter-repo --invert-paths --paths-from-file ..\filter.txt --force`

Als je nu in de log van deze repo kijkt dan zal je zien dat deze bestanden zijn weggehaald. Maar niet die in de eerste commit. 

- Voeg die nu ook toe.

```
bestand met secrets.txt
```
- Filter nogmaals de repo

    `git filter-repo --invert-paths --paths-from-file ..\filter.txt --force`

Je ziet dat nu niet alleen de bestanden weg zijn, maar zelfs de commits. Als er geen bestand in een commit meer zit, dan wordt deze volledig verwijderd!

## Repo met secrets

Je kan nu heel eenvoudig ook een opgeschoonde repo maken van alle bestanden met geheime info

- Kloon de bestaande repo:

    `git clone https://github.com/landrej/CleanGit.git private` 

- Filter nu de repo. Laat hierbij de parameter --invert-paths weg. Dit zorgt ervoor dat enkel de bestanden die in filter.txt staan worden bewaard.

    `git filter-repo --paths-from-file ..\filter.txt --force`

Voila, een opgeschoonde repo's met je donkerste geheimen er in.