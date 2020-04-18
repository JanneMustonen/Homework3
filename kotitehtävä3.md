##  kotitehtävä 3

**Tämä on teron kurssin kolmas kotitehtävä, joka toteutetaan gitillä ja lisätään sen jälkeen  githubiin.**

***

**a)**

Latasin **typora** markdown editorin linuxille, koska nano ei tue Markdown komentoja, joten päätin ladata uuden editorin.

 _wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -_

_sudo add-apt-repository 'deb https://typora.io/linux ./'_

_sudo apt-get update_

_sudo apt-get -y install typora_

***

**b)**

**git log** komennolla näet logi tiedot mitä ja milloin olet muokannut ja commit tiedostoon voi lisäsät kommentin mitä olet esim muokannut .

**git diff** näyttää tiedostojen sisällä tehdyt muutokset.

**git blame** näyttää kuka on tehnyt muutoksen/kirjoittanu tiedostoon tekstiä. Blame komento näyttää myös kellonajat milloin tiedostoon on tehty muutoksia/kirjoitettu

***

**e)**

Kirjoitin tiedostooni turhaa tekstiä, mutta en committanu tiedostoa, mutta pushasin sen githubiin ja tallenuksen jälkeen käytin **git reset --hard** komentoa ja se poisti turhat muutokset, jotka olin tehnyt ja se haki automaattisesti ennen muutoksia tehdyn version.

***

**f)**

Tässä tehtävässä aion asentaa fail2ban ohjelman, ja fail2ban ohjelmalla pystytään suojaamaan palvelinta tietystä IP-osoitteeata tulevaa hyökkäystä vastaan.

_Sudo apt-get -y install fail2ban_

Kopioin tiedoston **jail.conf** -> **jail.local** tiedostoksi. **Jail.local** tiedosto sisältää kaikki asetukset, mutta tämän tiedoston päälle saatetaan kirjoittaa päivitysten yhteydessä. Fail2ban lukee asetukset **jail.local** tiedostosta, jolloin **jail.conf** jää koskemattomaksi.

Kävin vaihtamassa asetuksia jail.local tiedostosta ja bannasin IP-osoitteen 10 minuutiksi 1 tunnin sijaan. Tämän jälkeen käynnistin ohjelman uudelleen.

_sudo systemctl restart fail2ban_

**Saltin automatisointi**

luodaan uusi directory **/srv/salt** kansioon eli **/srv/salt/fail2ban**

_sudo mkdir /srv/salt/fail2ban_

ja kopioidaan **/etc/fail2ban/jail.local** tiedosto **/srv/salt/fail2ban** kansioon

_sudo cp /etc/fail2ban/jail.local /srv/salt/fail2ban_

tämän jälkeen loin vielä sls tiedoston

_sudoedit /srv/salt/fail2ban.sls_

sls tiedostoon kirjoitettin

fail2ban:
  pkg.installed

/etc/fail2ban/jail.local:
  file.managed:
    -source: salt://fail2ban/jail.local

fail2banservice:
  service.running:
    -name: fail2ban

tämän jälkeen ajoin ohjelman 

_sudo salt '*' state.apply fail2ban_

Minulla kuitenkin ilmeni ongelmia kohdassa file.managed ja sain korjattua kohdan kopioimalla fail2ban.sls tiedoston kansiosta /srv/salt/fail2ban kansioon /srv/salt ja sain tämän toimimaan oikein.



Tehtävässä meni noin 3h

***

**Lähteet**

www.TeroKarvinen.com

www.hannukankkunen.wordpress.com/2018/12/10/palvelinten-hallinta-h3/





 

















​       

