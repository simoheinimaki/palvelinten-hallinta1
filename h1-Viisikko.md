# H1-Viisikko
Käytän tehtävässä Debian 12 Bookwormia Vagrantilla.
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

## Saltin asentaminen ja demonstrointi(Debian 12)

Aloitan asentamalle Debian 12 virtuaalikoneelleni Saltin [Salt Project - Install Guide](https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/linux-rpm.html#install-rpm):n mukaan. 
Ohjeessa käytetään "curl" komentoa. Jotta voin suorittaa asennuksen täysin ohjeiden mukaan, asennan ensin curlin koneelleni.

    sudo apt install curl

Tämän jälkeen jatkan saltin asennusta lataamalla public keyn ja repon:
![kuva](https://github.com/user-attachments/assets/174b05bb-b10c-4d76-a34b-1b839942b4fb)
![kuva](https://github.com/user-attachments/assets/bb230a8a-774b-4711-b674-0f2bddf9d3f9)
Sitten päivitän metadatan.

    sudo apt update

### b) Salt-minion asennus

    sudo apt-get install salt-minion

#### Tärkeimmät tilafunktiot
Käytän tilafunktioiden demonstroimiseen komentoja sivulta: [Run Salt Command Locally](https://terokarvinen.com/2021/salt-run-command-locally/)

##### pkg

    sudo salt-call --local -l info state.single pkg.installed tree

![kuva](https://github.com/user-attachments/assets/73cc98cc-9648-4995-9ced-5a8960002285)

Komennolla Tarkastetaan onko "Tree" asennettuna. Jos ei, "Tree" asennetaann tietokoneelle.

##### file

    sudo salt-call --local -l info state.single file.managed /tmp/hellotero

![kuva](https://github.com/user-attachments/assets/e586026c-bccb-428a-ab5a-33d9107b27b6)

Komennolla Tarkastetaan onko tiedostoa "/tmp/hellotero" olemassa. Jos ei, tiedosto luodaan automaattisesti.

##### service

    sudo salt-call --local -l info state.single service.running apache2 enable=True

![kuva](https://github.com/user-attachments/assets/75b438e7-f8e5-4633-b7e4-5f87f163263d)

Komennolla voi käynnistää daemoneita uudestaan. Komento epäonnistui, sillä minulla ei ole apache2 ollenkaan ladattuna.

##### user

    sudo salt-call --local -l info state.single user.present terote08

![kuva](https://github.com/user-attachments/assets/9711c5f4-3b86-4b0a-ac1e-da0b1bd9fdf7)

Komennolla Tarkastetaan onko käyttäjää "terote08" olemassa. Jos ei, käyttäjä luodaan.

##### cmd

    sudo salt-call --local -l info state.single cmd.run 'touch /tmp/foo' creates="/tmp/foo"

![kuva](https://github.com/user-attachments/assets/2c78a209-a49c-472d-b3b8-6c6e5d971c4f)

Komennolla ajettiin komento "touch /tmp/foo".
## Lähteet
Karvinen, Tero. 2023. [Run Salt Command Locally](https://terokarvinen.com/2021/salt-run-command-locally/). Luettu: 31.10.2024

Karvinen, Tero. 2018. [Salt Quickstart – Salt Stack Master and Slave on Ubuntu Linux](https://terokarvinen.com/2018/03/28/salt-quickstart-salt-stack-master-and-slave-on-ubuntu-linux/). Luettu: 31.10.2024

Karvinen, Tero. 2006. [Raportin kirjoittaminen](https://terokarvinen.com/2006/06/04/raportin-kirjoittaminen-4/). Luettu: 31.10.2024

https://docs.saltproject.io/salt/install-guide/en/latest/topics/install-by-operating-system/linux-deb.html. Luettu: 31.10.2024
