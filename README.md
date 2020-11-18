# Analiza podatkov s programom R, 2020/21

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2020/21

* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/ajdamajhenic/APPR-2020-21/master?urlpath=shiny/APPR-2020-21/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/ajdamajhenic/APPR-2020-21/master?urlpath=rstudio) RStudio

## Tematika: Analiza dejavnikov, ki vplivajo na okolje v Sloveniji

V tej projektni nalogi bom analizirala določene dejavnike, ki vplivajo na okolje v Sloveniji. Analizirala bom količine izpuščenih toplogrednih plinov v ozračje za različne gospodarske dejavnosti, nastale komunalne odpadke (nevarne, reciklirane), investicije za varstvo okolja in gospodarsko rast države. Ukvarjala se bom s podatki, pridobljenimi med letoma 2012 in 2018, vir pa bo stran statističnega urada Republike Slovenije (SURS).

Cilj analize je poiskati povezave med izpusti toplogrednih plinov, stopnjo recikliranja, z investicijami za varstvo okolja in rastjo BDP-ja.


TABELE:
1. tabela: letni izpusti toplogrednih plinov (CO2, N2O, CH4, SF6)
  * NAMEA emisije v zrak (SKD 2008) po: DEJAVNOST, MERITVE , LETO
  (https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/2719901S.px/table/tableView    Layout2/)
  
2. tabela: nastali komunalni odpadki, nastali nevarni komunalni odpadki, reciklirani komunalni odpadki
  * Kazalniki za odpadke po: KAZALNIKI , LETO
  (https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/2700001S.px/table/tableViewLayout2/)
  
3. tabela: investicije za varstvo okolja (v % BDP-ja), tekoči izdatki za varstvo okolja (v % BDP-ja), investicije za varstvo okolja v industriji (v % BDP-ja)
  * Investicije in tekoči izdatki za varstvo okolja (1000 EUR) po: LETO , VRSTA IZDATKA
  (https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/H004S.px/table/tableViewLayout2/)
  
4. tabela: BDP (količina, rast)
  * Proizvodna struktura BDP (SKD 2008) po: LETO, MERITVE, TRANSAKCIJE , DEJAVNOSTI/TRANSAKCIJE
  (https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/0301915S.px/table/tableViewLayout2/)



## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `tmap` - za izrisovanje zemljevidov
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-202021)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).
