# h5-Salt-windowsille

a) Ensiksi asennetaan SALT windowsille (Salt-Minion-3005.1-1-Py3-AMD64.msi), jonka jälkeen avataan PowerShell admin oikeuksilla.
Tämän jälkeen siirrytään oikeaan kansioon komennolla: cd C:\Users\jarkko\Lataukset 
Sen jälkeen asennetaan salt minion tiedosto.  ./Salt-Minion-3005.1-1-Py3-AMD64.msi

Asennuksen jälkeen testasin toimiiko salt-call --local cmd.run "echo hello world" tulosti hello world tekstin.
Ennen tekstitiedoston luomista luodaan salt kansio mkdir salt komennolla.
Kun kansio on luotu ja se näkyy järjestelmässä voidaan luoda suolaikkuna.txt tiedosto notepadin avulla.
"notepad.exe suolaikkuna.txt"
Notepad ikkuna avautuu ja voidaan kirjoittaa sinne mitä halutaan esim. Hello World
Sen jälkeen tarvitaan init.sls tiedosto notepadilla
tmp/salt:
  file.managed:
    - source: salt://suolaikkuna.txt
 
 tämän jälkeen ajetaan tiedosto komennolla salt-call --file-root=C:/Users/jarkko/srv/salt/suolaikkuna --local state.apply init
 Ja hurraa! Läpi meni pienten vastoinkäymisten jälkeen!
 
 b) Kerätään tietoja koneesta komennolla salt-call --local grains.items
 Yksinkertaisesti luodaan tekstitiedosto josta samat tiedot näkyvät komnennolla:
 salt-call --local grains.items > tiedot.txt
 tiedot.txt tekstitiedoston pitäisi nyt löytyä salt kansiosta. Vastaavan voi myös tarkistaa ls komennolla.
 
 c) Windowsilla komento "netstat -ano" tulostaa kaikki portit.
 Linuxilla komento sudo ss -tulpn
 
