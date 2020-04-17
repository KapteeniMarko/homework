# Homework 3

#### Tämä on Teron kurssille tehty kotitehtävä.

A) Latasimme Typoran jolla teimme .md tiedostoja. Testasimme ja harjoittelimme Typoran käyttöä sekä tiedostojen lähettämistä githubiin.

B) **__git log__** näyttää lokitiedot jossa näen mitä tiedostoja olen luonut ja muokannut, esimerkkinä:

Commit 289etcetcetc.

Author: Marko Nurmola <marko.nurmola@myy.haaga-helia.fi>

Date: Fri Apr 17 11:56:27 2020

Changes to be committed:

New file Homework3_Marko_Nurmola.md

**__git diff__** näyttää muutokset jotka on tehty tiedostojen sisälle, kuten 

-##Tämä on Teron kurssille tehty kotitehtävä

+#### Tämä on teron kurssille tehty kotitehtävä

Tässä oli alunperin kirjoitusvirhe, risuaidan ja Tämä sanan välistä puuttui väli jonka takia tein muutokset.

**git blame** komentoa voidaan käyttää että pääsee näkemään kuka on tehnyt muutokset tiettyyn riviin sekä milloin ne on tehty. Tällä on helppo syyttää jotain henkilöä hänen tekemistä muutoksista. Esimerkkinä suora rivi omasta terminalista jossa on käytetty **git blame**

34301157 (Marko Nurm 2020-04-17 12:31:50 +0300  1) # Homework 3

E) Kirjoitin turhaa tekstiä tiedostooni, en tehny committia ja käytin git reset -hard