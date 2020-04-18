# Homework 3

#### Tämä on Teron kurssille tehty kotitehtävä.

A) Latasimme Typoran jolla teimme .md tiedostoja. Testasimme ja harjoittelimme Typoran käyttöä sekä tiedostojen lähettämistä githubiin.

B) ***git log*** näyttää lokitiedot jossa näen mitä tiedostoja olen luonut ja muokannut, esimerkkinä:

Commit 289etcetcetc.

Author: Marko Nurmola <marko.nurmola@myy.haaga-helia.fi>

Date: Fri Apr 17 11:56:27 2020

Changes to be committed:

New file Homework3_Marko_Nurmola.md

***git diff*** näyttää muutokset jotka on tehty tiedostojen sisälle, kuten 

-##Tämä on Teron kurssille tehty kotitehtävä

+#### Tämä on teron kurssille tehty kotitehtävä

Tässä oli alunperin kirjoitusvirhe, risuaidan ja Tämä sanan välistä puuttui väli jonka takia tein muutokset.

***git blame*** komentoa voidaan käyttää että pääsee näkemään kuka on tehnyt muutokset tiettyyn riviin sekä milloin ne on tehty. Tällä on helppo syyttää jotain henkilöä hänen tekemistä muutoksista. Esimerkkinä suora rivi omasta terminalista jossa on käytetty ***git blame***

34301157 (Marko Nurm 2020-04-17 12:31:50 +0300  1) # Homework 3

E) Kirjoitin turhaa tekstiä tiedostooni, en tehny committia ja käytin ***git reset --hard*** komentoa joka poisti tekemäni turhat muutokset, sekä haki githubista viimeisimmän tallennetun version. Yllätyin tästä miten helppoa se oli.

F) Päätimme asentaa ohjelman nimeltä fail2ban jota voi käyttää esimerkiksi yksittäisten IP-osotteiden yhteydenoton estämiseen.

Aloitetaan ajamalla ***sudo apt-get -y install fail2ban***.

Tämän jälkeen kopioidaan jail.conf tiedosto samaan kansioon jail.local nimellä jolloin päivitykset eivät kirjoita sen päälle jos haluamme tehdä muutoksia. Komento tähän on ***sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local***

 Kun aloitamme automatisoidun asennuksen, meidän täytyy ensiksi luoda oma kansio fail2banille /srv/salt/ kansioon, tähän käytetään komentoa ***sudo mkdir /srv/salt/fail2ban/*** kopioida jail.local tiedosto saltille komennolla ***sudo cp /etc/fail2ban/jail.local /srv/salt/fail2ban/*** 

Kun olemme tämän tehneet, käytämme komentoa ***sudoedit /srv/salt/fail2ban.sls*** johon kirjoitamme taas YAML-koodina tämän kaiken 

**fail2ban:**
  **pkg.installed**

**/etc/fail2ban/jail.local:**
  **file.managed:**
    **– source: salt://fail2ban/jail.local**

**fail2banservice:**
  **service.running:**
    **– name: fail2ban**
    **– file: /etc/fail2ban/jail.local**

Tämän jälkeen vain käytämme komentoa ***sudo salt '*' state.highstate***

Tämän jälkeen käytin sudo salt '*' state.apply fail2ban jonka jälkeen kaikki onnistui hyvin. Tässä kopio että kaikki onnistui hyvin. (En osaa vielä lisätä kuvia.)

make:
----------
          ID: fail2ban
    Function: pkg.installed
      Result: True
     Comment: All specified packages are already installed
     Started: 12:38:47.568702
    Duration: 931.353 ms
     Changes:   
----------
          ID: /etc/fail2ban/jail.local
    Function: file.managed
      Result: True
     Comment: File /etc/fail2ban/jail.local is in the correct state
     Started: 12:38:48.503703
    Duration: 20.081 ms
     Changes:   
----------
          ID: fail2banservice
    Function: service.running
        Name: fail2ban
      Result: True
     Comment: The service fail2ban is already running
     Started: 12:38:48.551862
    Duration: 35.048 ms
     Changes:   

Summary for make
------------
Succeeded: 3
Failed:    0
------------
Total states run:     3
Total run time: 986.482 ms



Aikaa näihin tehtäviin meni noin 4.5h koska tiedonkerääminen sekä uusien asioiden opettelu vei aikaa.

Lähteinä on käytetty:

https://hannukankkunen.wordpress.com/2018/12/10/palvelinten-hallinta-h3/

https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet

http://terokarvinen.com/2020/configuration-managment-systems-palvelinten-hallinta-ict4tn022-spring-2020/

