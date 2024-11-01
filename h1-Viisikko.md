# H1-Viisikko
## Tiivistelmät
### Run Salt Command Locally
- Salt:ia käytetään useiden slave-tietokoneiden hallintaan.
- Tärkeimmät tilafunktiot ovat: pkg, file, service, user, cmd.
- Linuxissa kaikki asetukset ovat tekstitiedostoja

### Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux
- Slaven täytyy tietää masterin osoite.
- Joka slavella oltava eri id.
- Slave yhdistettävä masteriin IP-osoitteella.
- Master hyväksyy Slave key:n
- Jos Slave vastaa, se toimii.

  Salt Master asentaminen Linux:
  
        $ sudo apt-get update
        $ sudo apt-get -y install salt-master

  Salt Slave asentaminen Linux:

        $ sudo apt-get update
        $ sudo apt-get -y install salt-minion

  Slaven yhdistäminen masteriin:

        $ sudoedit /etc/salt/minion

  Yhdistämisen jälkeen käynnistä slave uudestaan:

        $ sudo systemctl restart salt-minion.service

  Slave Keyn Hyväksyntä:

        $ sudo salt-key -A

### Raportin kirjoittaminen
- Kirjoita raporttia samalla kun teet.
- Raportin on oltava täsmällinen.
- Kerro tarkkaan mikä onnistui tai epäonnistui.
- Viittaa lähteisiin.
- Plagiointi rangaistavaa.

## Lähteet
Karvinen, Tero. 2023. [Run Salt Command Locally](https://terokarvinen.com/2021/salt-run-command-locally/). Luettu: 31.10.2024

Karvinen, Tero. 2018. [Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux](https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/). Luettu: 31.10.2024

Karvinen, Tero. 2006. [Raportin kirjoittaminen](https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/). Luettu: 31.10.2024
