##  kotitehtävä 3

**Tämä on teron kurssin kolmas kotitehtävä, joka toteutetaan gitillä ja lisätään sen jälkeen lisätään githubiin.**

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

















​       

