# Eesti juhiload

Eestis võib mootorsõidukit juhtida isik, kellel on vastava kategooria sõiduki juhtimise õigus.
Juhtimisõiguse tõendamiseks väljastatakse isikule Euroopa Liidu mudeli kohane juhiluba.

Käesolev andmestik annab ülevaate Eestis antud kuupäeva seisuga kehtivatest juhilubadest.

Vaata ka:

- [Transpordiamet - Juhiluba](https://www.transpordiamet.ee/juhiluba)
- [Riigi Teataja - Juhi eksamineerimine ja juhtimisõiguse andmine](https://www.riigiteataja.ee/akt/128062011018?leiaKehtiv)
  - Lisa 18: Juhiloa tagaküljele kantavad koodid

## Andmestikus olevad failid

- `jl_<kuupäev>.csv` - Kehtivad juhiload vastaval kuupäeval
- `jl_<kuupäev>.csv töödeldud` - Avaandmete poolt töödeldud versioon failist; API tarbimine võib töötada, aga ei soovita faili ennast alla laadida
- `jl_metadata.json` - Veerupõhised metaandmed jl csv failide kohta, mis peaks olema ka kättesaadav kui tarbida andmeid läbi API

## Andmete kuju

Igal real on üks vastaval ajahetkel kehtiv juhiluba:

- `Loa number` - Juhiloa numbri esimesed 3 märki, üldiselt on selleks kahetäheline seeria + üks number (väli 5)
- `Loa tüüp` - Kas tegu on esmase või tavalise juhiloaga
- `Kehtiv alates` - Kehtivuse alguse aasta ja kuu, alati varasem kui faili ajahetk (väli 4a)
- `Kehtiv kuni` - Kehtivuse lõpu aasta ja kuu, alati hilisem kui faili ajahetk (väli 4b)
- `Kategooriad` - Kategooriad, millega tohib sõita; sorteeritud ja tühikutega eraldatud (väli 9)
- `Kategooria lisaandmed` - Eritingimused, mis kehtivad ühele kategooriale kujul {kat}:{tingimuse üldosa} (märkus 79 puhul on ka sisu kaasas), sorteeritud ja eraldatud püstkriipsudega (väli 12)
  - Väljade 12 ja 14 sisu seletus on eelnevalt mainitud akti lisas 18
- `Lisaandmed` - Eritingimused, mis kehtivad kõikidele kategooriatele; ainult tingimuse üldosad, sorteeritud ja püstkriipsudega eraldatud (väli 12)
- `Väli 14` - Eritingimused, lähevad 14. väljale; hetkel ainult A kategooria märkus 105 (väli 14)
- `Sünniaasta` - Loa omaniku sünniaasta (väli 3)
- `Sugu` - Sugu isikukoodi põhjal juhul kui isikukoodi sünniaeg klapib isiku sünniajaga baasis (M-Mees/N-Naine)
- `Taotluse büroo` - Büroo, kus esitati juhiloa taotlus
- `Väljastaja büroo` - Büroo, kus väljastati juhiluba (või märge, et saadeti postiga)
- `Kiirluba` - Kas luba telliti kiirtellimusena (J-Jah/E-Ei)

## Andmete Excelisse importimine

Seda faili ei ole soovitatav topelt klõpsuga eestipärases Excelis avada: ta ei oska sellega midagi peale hakata (muu regiooni Excelis võib minna paremini).

Parima tulemuse jaoks:

- Ava Excelis tühi töövihik
- Vali Andmed - Too andmed - Failist - Teksti-/CSV-failist
- Impordi soovitud `jl_<kuupäev>.csv` fail
- Määra õiged parameetrid:
  - Faili päritolu: `65001: Unicode (UTF-8)`
  - Eraldaja: Koma
- Klõpsa "Andmeid transformeerima"
  - Klõpsa "Kasuta esimest rida päistena" kui "Esiletõstetud päised" ei ole juba etappides
  - Kontrolli üle, et andmetüübid on õiged
    - Andmetüübi muutmiseks klõpsa veeru nimest vasakule jäävat tüübi ikooni
    - Lisaandmed peab olema teksti kujul, ülejäänud leiab Excel ilmselt ise üles
    - (Kehtivuste puhul Excel automaatselt märgib kõik ajad esimesele päevale kui selle tüübiks on valitud kuupäev, tegelikult on antud ainult aasta ja kuu)
  - Klõpsa "Sule ja laadi"
- Kui "Päringud ja ühendused" kaardil ei ole näha ühtegi tõrget, siis läks laadimine loodetavasti edukalt

## Avaandmete lehe masintöötlusest

- Avaandmete leht nõuab pealkirja ja kirjeldust nii eesti kui inglise keeles, aga ikkagi automaatselt tõlgib eestikeelse teksti ingliskeelseks ja siis veel on tal jultumust öelda et "Metaandmete tõlkimiseks on kasutatud masintõlget ning nende kvaliteet võib seega olla kohati ebakorrektne"
- Failide järjekord ei ole sama kui üleslaadimise järjekord; ma ei tea miks ta neid sellises järjekorras näitab
- Ära lae alla töödeldud faili
  - Abivalmilt pannakse igale väärtusele jutumärgid ümber, ehk fail läheb suuremaks ja midagi ei muutu paremaks
  - Veerud järjestatakse ümber mingis järjekorras, sest see polnud ju tähtis kuidas need algselt olid, ega ju?
  - Kui laadida csv fail üles läbi veebilehe (mitte API), siis lähevad andmed veel rohkem katki; aga selle detailid jätaksin juba lugeja avastada

# Estonian driving licences

In Estonia, a person may drive a motor vehicle if they have the right to drive a vehicle of the equivalent category.
To prove the right to drive, a person issued a European driving licence.

This dataset gives an overview of valid driving licences on a given date.

See also:

- [Transportation Administration - Driving licence](https://www.transpordiamet.ee/en/mobility-and-transportation/driving-licence-and-right-drive)
- [Riigi Teataja - Driver examination and assigning the right to drive](https://www.riigiteataja.ee/akt/128062011018?leiaKehtiv) (probably only in Estonian) (if you find this act in English on their website, please let us know so it can be added here)
  - Annex 18: Codes on the back side of a driving licence

## Files in the dataset

- `jl_<date>.csv` - Active licences on a given date
- `jl_<date>.csv processed` - Version of the file that has been processed by the open data website; consuming via API may work, but downloading this file is not advised
- `jl_metadata.json` - Column-based metadata about jl csv files which should also be available via API

## Data structure

Every row contains one driving licence that is active on a given date:

- `Loa number` - First 3 characters of the number of the licence, generally this is the two-letter series + one digit (field 5)
- `Loa tüüp` - If the licence is a provisional or normal licence
- `Kehtiv alates` - Year and month of the start of validity (field 4a)
- `Kehtiv kuni` - Year and month of the end of validity (field 4b)
- `Kategooriad` - Categories that can be driven; sorted and delimited by vertical lines (field 9)
- `Kategooria lisaandmed` - Additional information about specific categories in the form {cat}:{info header} (for 79 the details are also included), sorted and delimited by vertical lines (field 12)
  - Explanations for codes in fields 12 and 14 can be found in annex 18 of the previously mentioned act
- `Lisaandmed` - Additional information about all categories; only info headers, sorted and delimited by vertical lines (field 12)
- `Väli 14` - Additional information on field 14; currently only category A info 105 (field 14)
- `Sünniaasta` - Birth year of licence owner (field 3)
- `Sugu` - Gender based on national identification number if birth date matches id number birth date in the database (M-Male/N-Female)
- `Taotluse büroo` - Bureau where the licence application was submitted
- `Väljastaja büroo` - Bureau where the licence was issued (or note that it was sent by mail)
- `Kiirluba` - If the licence was ordered with a faster delivery time (J-Yes/E-No)

## Importing data into Excel

This file is not recommended to be opened in Estonian regional Excel by way of double clicking on it (other flavors that respect comma as a delimiter may fare better).

For best results (keep in mind I do not have English language Excel and some labels may be different):

- Open an empty spreadsheet in Excel
- Click on Data - Get Data - From File - From Text/CSV
- Import the desired `jl_<date>.csv` file
- Pick the correct parameters:
  - File Origin: `65001: Unicode (UTF-8)`
  - Delimiter: Comma
- Click "Transform Data"
  - Click "Use First Row as Header" if such a step is not already in applied steps
  - Check that column types are correct
    - To change type, click the type icon to the left of the column name, pick a type, and click "Replace current" in the window that opens
    - Lisaandmed must be text, the rest should be fine automatically
    - (for validity dates, Excel will automatically mark every date as happening on the first of the month if date type is picked, even though the actual data only contains year and month)
  - Click "Close & Load"
- If the card on the right does not show any issues, then hopefully the loading was successful

## About Estonian open data machine processing

- The open data page requires a title and description both in Estonian and English, but then proceeds to overwrite the English text with an automatic translation; it then has the gall to say "Metadata is machine translated and may thus be of poor quality"
- The ordering of files is not the same as the order they were uploaded; I have no idea what order this is
- Do not download a processed file
  - Ever-so-helpfully every value gets quotation marks around it, which only serves to inflate the file size and do nothing else
  - Columns are reordered in some god-only-knows order, because it's not like that was an important part of the file that you spent time designing, right?
  - If you upload a csv file through the website (not the API), then the data is even more broken; but the details of that shall be left to the reader to discover
