## System engineering

### ==Milyen virtualizációs technológiákat ismersz?
What kind of virtualization technologies are you familiar with?==
    
1. Teljes rendszer-virtuálizáció: Ez a virtuálizációs forma az egész operációs rendszert virtualizálja. Egy teljes virtuális gép létrehozásával lehetővé teszi, hogy az operációs rendszer és az alkalmazások elszigetelten fussanak a gazda rendszeren. Például a VMware Workstation és az Oracle VirtualBox ilyen típusú virtuálizációt kínál.
    
2. Konténerizáció: A konténerizáció technológiája a rendszer szintű virtualizáció alternatívája, amely a folyamatok elkülönítésén alapul. A konténerek segítségével alkalmazásokat lehet izolálni és futtatni egy közös operációs rendszeren belül, ezáltal hatékonyabb erőforrásfelhasználást biztosítva. A Docker egy népszerű konténerizációs platform. Ebben az estben a host gép kerneljét fogja használni a futtatásokra és a management szolgáltatásokra.


### ==Mennyire vagy jártas a virtuálizációs megvalósítások szintjében?
What level of virtualization implementations are you familiar with?==



  
### ==Milyen parancssoros szövegmanipulációs eszközökkel vagy jártas?
What command line text manipulation tools are you familiar with?==

1. grep: A grep parancs segítségével szövegmintákra lehet keresni és kiválasztani a szöveges fájlokban.
    
2. sed: Az sed parancs lehetővé teszi a szöveges adatok átalakítását és módosítását. Különböző szöveges műveletek, például cserék, törlések és beillesztések végezhetők vele.
    
3. awk: Az awk egy erőteljes szövegfeldolgozási eszköz, amely soronként dolgozza fel a bemeneti adatokat, és lehetőséget nyújt a szöveges oszlopok manipulálására és feldolgozására.
    
4. cut: A cut parancs segítségével lehetőség van kivágni (vágni) a sorokból és oszlopokból adott karaktereket vagy tartományokat.
    
5. tr: A tr parancs karakterek cseréjét és törlését teszi lehetővé a bemeneti szövegben. Használható például karakterek konvertálására vagy cenzúrázására.
    
6. sort: A sort parancs segítségével lehet sorrendbe rendezni a bemeneti szöveget soronként vagy oszloponként.
    
7. uniq: Az uniq parancs megszűnteti az egymást követő ismétlődő sorokat a bemeneti szövegben, vagy csak az ismétlődő sorokat hagyja meg, attól függően, hogy hogyan van konfigurálva.


### ==Hogyan hoznál létre egy ütemezett parancsot, amely minden vasárnap éjfélkor futna?
How would you create scheduled command command to run every sunday at midnight?==


Linux rendszeren a `cron` szolgáltatás segítségével lehet ütemezett parancsokat létrehozni. A következő lépésekkel hozhatsz létre egy ütemezett parancsot, amely minden vasárnap éjfélkor fog futni:

1. Nyisd meg a terminált vagy SSH-kapcsolatot a Linux rendszerrel.

2. Írd be a következő parancsot a `crontab` parancssorba, hogy szerkesztheted a felhasználói `crontab` fájlt:
```
crontab -e
```

3. Ezután a rendszer megnyitja a `crontab` fájlt szerkesztésre. Ha először hozol létre ütemezést, akkor kérheti, hogy válassz egy alapértelmezett szövegszerkesztőt.

4. A szövegszerkesztőben navigálj a fájl végére, majd írd be a következő sort:
```
0 0 * * 0 <parancs>
```
Ez a sor azt jelenti, hogy minden vasárnap (`0 0 * * 0`) éjfélkor (`0 0`) fog futni a megadott `<parancs>`. A `0`-ás értékek a perc és az óra, és a `*` jelöl minden napot/hetet/hónapot.

Ebben a sorban az öt mező a tervezési információkat jelöli:

- Az első mező `0` reprezentálja a percet (0-59).
- A második mező `0` reprezentálja az órát (0-23).
- A harmadik mező `*` reprezentálja a hónap napját (1-31).
- A negyedik mező `*` reprezentálja a hónapot (1-12).
- Az ötödik mező `0` reprezentálja a hét napját (0-7), ahol mind a 0, mind a 7 a vasárnapot jelöli.

5. Cseréld ki a `<parancs>` részt a tényleges parancsra, amit végrehajtani szeretnél. Győződj meg róla, hogy a parancs teljes elérési útvonallal rendelkezik, például `/usr/bin/parancs`. Ha több parancsot szeretnél futtatni, akkor használj pontosvesszőt (`;`) a parancsok között.

6. Mentéshez és bezáráshoz a szövegszerkesztőben kövesd az adott szövegszerkesztő specifikus parancsokat.

7. A `crontab` fájl elmentése után a rendszer automatikusan aktiválja az ütemezett parancsot, és minden vasárnap éjfélkor futni fog.

Fontos megjegyezni, hogy a `cron` ütemezett parancsokat a rendszer időzónájához igazítja, ezért bizonyos esetekben ellenőrizd az időzóna beállításait a helyes ütemezés érdekében.



### ==Hogyan ellenőriznéd a rendelkezésre álló szabad memóriát?
How would you check the available free memories?==


`free -h` parancs:
   - Nyiss meg egy terminált és futtasd a `free` parancsot kapcsolók nélkül.
   - Ez a parancs megjeleníti a rendszer memóriahasználatát és elérhetőségét.
   - Az `-h` kapcsoló a méreteknek megfelelő egységeket használ (például GB, MB) a jobb olvashatóság érdekében.
   - A kimenet információt nyújt a teljes, használt és szabad memóriáról kilobájtban (KB).
   - Itt van egy példa kimenet:

```
              teljes     használt      szabad     megosztott  buff/cache  rendelkezésre álló
Mem:        2048000     1200000      248000       96000      600000      784000
Swap:        524288      120000      404288
```




### ==Hogyan ellenőriznéd a rendelkezésre álló szabad lemezterületet a számítógépen?
How would you check the available free disk space on the computer?==


A rendelkezésre álló szabad lemezterület ellenőrzéséhez egy Linux számítógépen használhatod a `df` parancsot. Így teheted meg:

Nyiss meg egy terminált és írd be a következő parancsot:

```
df -h
```

Ez az parancs emberi olvasható formában jeleníti meg a lemezhasználati információkat, gigabájt (GB) vagy megabájt (MB) méretekben, nem pedig az alapértelmezett kilobájtokban (KB).

A kimenet több sorból áll, mindegyik egy különböző fájlrendszer vagy partíció. Az "Available" oszlop mutatja az ingyenes hely mennyiségét minden partíción.

Itt van egy példa kimenet:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   30G  40% /
/dev/sdb1       100G   50G   50G  50% /home
```

Ebben a példában a gyökér fájlrendszer ("/") rendelkezik 30 gigabájtnyi (GB) szabad hellyel, míg a "/home" partíció 50 GB szabad hellyel rendelkezik.

A `df` parancs használható a `--total` kapcsolóval is, hogy összegző információkat kapj a lemezhasználatról és a szabad helyről az összes partíción:

```
df -h --total
```

Ez az utasítás a kimenet alján egy összesítő sort jelenít meg, amelyben látható a teljes lemezterület, a teljesen használt hely, a teljes szabad hely és az összesített használati arány.


### ==Mi a különbség a merev hivatkozások (hard links) és a szimbolikus hivatkozások (symbolic links) között?
What are hard links and symbolic links?==


A merev hivatkozások (hard links) és a szimbolikus hivatkozások (symbolic links) mindkettő fájlrendszeri hivatkozások, amelyeket operációs rendszerekben használnak a fájlok közötti kapcsolatok létrehozására. Azonban eltérnek abban, hogyan működnek és milyen típusú fájlokra hivatkozhatnak.

1. Merev hivatkozások (Hard links):
   - A merev hivatkozás közvetlen hivatkozás egy fájlra vagy könyvtárra a fájlrendszerben.
   - Új fájlbejegyzést hoz létre, amely ugyanarra az alap adatra mutat, mint az eredeti fájl.
   - Az összes merev hivatkozás az adott fájlra lényegében egyenlő, nincs fogalom a "forrás" vagy "cél" fájlra vonatkozóan.
   - Egy merev hivatkozás törlése nem érinti az eredeti fájlt, amíg más merev hivatkozások is léteznek rá.
   - Merev hivatkozások nem terjedhetnek ki különböző fájlrendszerekre vagy partíciókra.

2. Szimbolikus hivatkozások (Soft Links):
   - Egy szimbolikus hivatkozás, más néven lágy hivatkozás, egy speciális fájltípus, amely más fájlra vagy könyvtárra hivatkozik az útvonalával.
   - Nem közvetlenül az eredeti fájl adatára mutat, hanem tartalmazza a célfájl vagy könyvtár elérési útvonalát.
   - Szimbolikus hivatkozások pointerként vagy gyorsbillentyűként működnek a célfájlra vagy könyvtárra.
   - Ha az eredeti fájl vagy könyvtár törlődik vagy áthelyezik, a szimbolikus hivatkozás megszakad és nem oldható fel.
   - Szimbolikus hivatkozások átívelhetnek különböző fájlrendszereken vagy partíciókon.

Összefoglalva, a merev hivatkozások új fájlbejegyzéseket hoznak létre, amelyek ugyanarra az alapadatra mutatnak, míg a szimbolikus hivatkozások fájlokat tartalmaznak, amelyek az útvonalukon keresztül hivatkoznak más fájlokra vagy könyvtárakra. A merev hivatkozások nem terjedhetnek ki fájlrendszereken keresztül, míg a szimbolikus hivatkozások igen. Emellett a merev hivatkozás törlése nem érinti az eredeti fájlt, míg a szimbolikus hivatkozás törlése megszakíthatja a kapcsolatot a célfájlhoz.




### ==Hogyan állíthatnád be, hogy egy szolgáltatás automatikusan induljon el és rendszerindításkor betöltődjön?
How would you make a service auto-start and machine boot-up==


Ahhoz, hogy egy szolgáltatás automatikusan elinduljon a Linux rendszer betöltésekor, általában a következő lépéseket kell végrehajtanod:

1. Hozz létre egy systemd szolgáltatás egységfájlt:
   - Nyiss meg egy szövegszerkesztőt root jogosultságokkal (pl. `sudo` vagy `su` használatával).
   - Hozz létre egy új fájlt `.service` kiterjesztéssel a `/etc/systemd/system/` könyvtárban. Például: `my-service.service`.
   - Ebben a fájlban határozd meg a szolgáltatást a nevével, leírásával, indítási viselkedésével és a végrehajtandó parancsával.
   - Itt van egy példa egy alap szolgáltatás egységfájlra:

```plaintext
[Unit]
Description=My Service
After=network.target

[Service]
ExecStart=/path/to/your/service/command

[Install]
WantedBy=default.target
```

Cseréld ki a `/path/to/your/service/command` részt a tényleges parancssal vagy szkripttel, amely elindítja a szolgáltatásodat.

2. Mentsd el a szolgáltatás egységfájlát és lépj ki a szövegszerkesztőből.

3. Engedélyezd a szolgáltatást:
   - A terminálban futtasd a következő parancsot root jogosultságokkal:

```bash
sudo systemctl enable my-service
```

Cseréld ki a `my-service` részt a szolgáltatás egységfájl nevével, a `.service` kiterjesztés nélkül.

4. Indítsd el a szolgáltatást:
   - A szolgáltatás azonnali indításához futtasd a következő parancsot:

```bash
sudo systemctl start my-service
```

5. Ellenőrizd a szolgáltatás állapotát:
   - Ellenőrizheted a szolgáltatás állapotát a következő paranccsal:

```bash
systemctl status my-service
```

Ez megjeleníti a szolgáltatásról szóló információkat, beleértve annak aktív (futó) vagy inaktív státuszát.

Ezeket a lépéseket követően a szolgáltatásod automatikusan el kell induljon a rendszer betöltésekor. A szolgáltatást manuálisan is vezérelheted a `start`, `stop`, `restart` és `status` parancsokkal a `systemctl` segítségével.


## Network engineering

### ==Mi az MAC-cím (Media Access Control cím)?
What is a MAC address?==

A MAC-cím (Media Access Control cím) egy egyedi azonosító, amelyet a hálózati eszközök, például számítógépek, okostelefonok vagy nyomtatók használnak a hálózati kommunikáció során. Ez a fizikai cím a hálózati interfészen található és gyárilag hozzárendelik az eszközhöz. A MAC-cím általában hat byte hosszú, és hexadecimális formában jelenik meg. Az első három byte a gyártót, míg a második három byte az adott eszközt azonosítja a hálózaton. A MAC-cím használata segít az eszközöknek azonosítani és kommunikálni egymással a helyi hálózaton.



### ==Mi a különbség a 127.0.0.1 és a 0.0.0.0 címhez való kötés között?
What is the difference between binding to 127.0.0.1 or 0.0.0.0?==

A 127.0.0.1 és a 0.0.0.0 IP-címekhez való kötés közötti különbség a következő:

- 127.0.0.1: Ez az IP-cím a loopback interfészt jelöli, ami azt jelenti, hogy a hálózati forgalmat visszatükrözi az adott eszközön belül. Amikor egy szolgáltatás vagy alkalmazás a 127.0.0.1 címhez köt, csak a helyi gépen tudja elérni és válaszolni a kérésekre. Más eszközökről nem érhető el.

- 0.0.0.0: Ez az IP-cím az összes hálózati interfészt jelenti az adott eszközön. Amikor egy szolgáltatás vagy alkalmazás a 0.0.0.0 címhez köt, az azt jelenti, hogy bármely hálózati interfészen elérhető lesz. Ez lehetővé teszi, hogy más eszközökről is elérhető legyen a szolgáltatás vagy alkalmazás.

Összefoglalva, a 127.0.0.1 címhez való kötés csak a helyi gépen történő hozzáférést engedi, míg a 0.0.0.0 címhez való kötés lehetővé teszi a szolgáltatás vagy alkalmazás elérését más eszközökről is a hálózaton.


### ==Melyek az OSI modell rétegei?
What are the Layers of the OSI model?==

1. Fizikai réteg (**Physical Layer**): Ez a legalsó réteg, amely az adatok fizikai átvitelével foglalkozik. Ide tartoznak az adatok bit formában történő átvitele, az adatkábelek, csatlakozók, fizikai jellemzők stb.

2. Adatkapcsolati réteg (**Data Link Layer**): Ez a réteg az adatok továbbítását biztosítja a hálózaton keresztül. A csomagokat keretekre bontja és ellenőrzi a hibákat a fizikai átvitel során.

3. Hálózati réteg (**Network Layer**): A hálózati réteg az adatok útvonalválasztásáért és a hálózati kapcsolatok kezeléséért felelős. Ide tartozik a csomagok továbbítása a hálózaton keresztül, valamint az IP-címzés és az útvonalválasztó protokollok kezelése.

4. Szállítási réteg (**Transport Layer**): Ez a réteg az adatok megbízható átviteléért felelős a forrás és a cél között. Ide tartoznak a megbízható adatátviteli protokollok, például a TCP (Transmission Control Protocol).

5. Munkamenet réteg (**Session Layer**): A munkamenet réteg biztosítja a kommunikációt két végpont között. Ez a réteg kezeli a kapcsolatot és a munkamenet azonosítóját a kommunikáció során.

6. Megjelenítési réteg (**Presentation Layer**): Ez a réteg adatainak formátumát és kódolását kezeli, hogy azok kompatibilisek legyenek a különböző rendszerek között. Ide tartozik az adatok karakterkódolása, tömörítése, titkosítása stb.

7. Alkalmazási réteg (**Application Layer**): Ez a legfelső réteg, amely közvetlenül az alkalmazásokkal és a felhasználóval kommunikál. Ide tartoznak az alkalmazások és szolgáltatások, például az e-mail, a webböngésző, a fájlmegosztás stb.

Ezek a rétegek hierarchikusan épülnek egymásra, és együtt alkotják az OSI modellt, amely segít az adatok hatékony és megbízható átvitelében a hálózatokban.


### ==Milyen a különbség egy router és egy switch között?
What is the difference between a router and switch?==

Router:
- A router egy hálózati eszköz, amely kapcsolatot biztosít két vagy több hálózat között.
- Feladata az adatok továbbítása a legoptimálisabb útvonalon a célhálózat felé.
- Az IP-címek alapján dönti el, hogy melyik csomagot kell továbbítani a megfelelő hálózatba.
- Képes szegmentálni és címezni a hálózatot, valamint biztonsági funkciókat is ellát, például tűzfalakat és portforwardingot.
- Alapvetően a szélessávú internetkapcsolatok és a WAN (Wide Area Network) kapcsolatok kezelésére használják.

Switch:
- A switch egy hálózati eszköz, amely csatlakoztatja a különböző eszközöket egy helyi hálózaton belül.
- Feladata a hálózati forgalom irányítása és a csomagok továbbítása a megfelelő eszközök között.
- A MAC-címek alapján dönti el, hogy melyik portra kell továbbítani a csomagot a célhoz.
- Gyakran használják Ethernet hálózatokban, például otthoni vagy irodai helyi hálózatokban.
- Nagyobb adatforgalmat képes kezelni és nagyobb hálózati sávszélességet biztosít a csatlakoztatott eszközök között.

Összefoglalva, a router a hálózatok közötti kapcsolatot kezeli, míg a switch a helyi hálózaton belüli adatok továbbítását végzi a csatlakoztatott eszközök között.


### ==Mi a router?
What is a Router==

A router egy hálózati eszköz, amely kapcsolatot biztosít két vagy több hálózat között. A router feladata az adatok továbbítása a legoptimálisabb útvonalon a célhálózat felé. Ez az eszköz képes szegmentálni és címezni a hálózatot, valamint biztonsági funkciókat ellátni, például tűzfalakat és portforwardingot. A routerek alapvetően a szélessávú internetkapcsolatok és a Wide Area Network (WAN) kapcsolatok kezelésére használatosak.


#### ==Hogyan működik a Router?
How Does a Router Work?==


A router működése röviden:

1. Címzés: A router kapcsolatot létesít több hálózat között. Minden hálózatot IP-címekkel azonosít, és döntéseket hoz arról, hogy melyik csomagot továbbítsa a megfelelő hálózatba.

2. Csomagok továbbítása: Amikor egy csomag érkezik a routerhez, ellenőrzi a címét, és megnézi, hogy a célhálózat azonos vagy más hálózatba tartozik-e. Ha a célhálózat más hálózatba tartozik, a router továbbítja a csomagot a megfelelő kimeneti interfészre a célhálózatba való eljuttatás érdekében.

3. Útvonalválasztás: A router egy belső útválasztási táblázatot használ, amely tartalmazza a hálózatok közötti kapcsolatokat és az optimális útvonalakat. Az útválasztási protokollok segítségével a router folyamatosan frissíti és megosztja ezeket az információkat más routerekkel a hálózaton.

4. Biztonság: A router biztonsági funkciókat is ellát, például tűzfalakat, portforwardingot és hálózati címezést. Ezek a funkciók segítenek védeni a hálózatot a nem kívánt behatolásoktól és megakadályozzák a káros adatok bejutását a hálózatba.

Összességében a router a hálózati forgalom irányításáért felelős eszköz, amely lehetővé teszi a kommunikációt és az adatok hatékony továbbítását különböző hálózatok között.



### ==Mi a Switch?
What is a Switch?

Egy switch egy hálózati eszköz, amely csatlakoztatja a különböző eszközöket egy helyi hálózaton belül. A switch feladata a hálózati forgalom irányítása és a csomagok továbbítása a megfelelő eszközök között. Ez az eszköz a MAC-címek alapján dönti el, hogy melyik portra kell továbbítani a csomagot a célhoz.



### ==Hogyan Működik a Switch?==

A switch működése a következőképpen zajlik:

1. Csomagok továbbítása: Amikor egy csomag érkezik a switch-hez, a switch megvizsgálja a csomagban található MAC-címet, amely egyedi azonosítója a hálózati eszköznek. A switch megnézi a saját belső táblázatát, amely tartalmazza a MAC-címek és a hozzájuk tartozó portok párosítását.
    
2. Portok kezelése: A switch megfelelően továbbítja a csomagot a táblázat alapján a megfelelő portra. Ha a switch nem ismeri fel a címzett MAC-címet, akkor a csomagot minden portra továbbítja, kivéve a forrásportot.
    
3. Címzett megtalálása: Amikor a csomag elér a célhálózati eszközhöz, a switch továbbítja azt a megfelelő porton keresztül, és a címzett eszköz megkapja a csomagot.
    

A switch működése lehetővé teszi a helyi hálózati eszközök közötti gyors és hatékony adatátvitelt. Ez különösen hasznos a helyi hálózatokban, ahol több eszköz kapcsolódik egymáshoz. A switch képes a hálózati sávszélesség hatékonyabb felosztására és a csomagok célhoz juttatására a megfelelő eszközökhöz.



### ==Mi a különbség a TCP és az UDP között?
What is the difference between TCP and UDP?==


TCP (Transmission Control Protocol):
- Kapcsolatalapú protokoll, amely megbízható adatátvitelt biztosít.
- A kapcsolat kiépítéséhez és fenntartásához háromlépcsős kézfogásra (hand shake) van szükség.
- Az adatokat sorrendben és hibamentesen szállítja a célhoz.
- Az adatok megerősítését és újraküldését biztosítja hibák és veszteségek esetén.
- Használja a puffereket és az áramvonalasítást a hatékony adatátvitel érdekében.
- Példák: weboldalak, e-mail, fájlátvitel.

UDP (User Datagram Protocol):
- Kapcsolat nélküli protokoll, amely nem biztosít megbízható adatátvitelt.
- Nincs szükség kapcsolat kiépítésére vagy fenntartására.
- Az adatokat nem garantálja sorrendben vagy hibamentesen.
- Nem nyújt megerősítést vagy újraküldést hibák vagy veszteségek esetén.
- Nincs pufferelés vagy áramvonalasítás, így a továbbítás minimális késleltetéssel történik.
- Példák: video streaming, hanghívások, DNS kérések.

Összefoglalva, a TCP megbízható és sorrendben történő adatátvitelt biztosít, míg az UDP gyorsabb és kapcsolat nélküli, de nem garantálja az adatok megbízhatóságát és sorrendjét. A választott protokoll az alkalmazás jellegétől és a prioritásoktól függ.



### ==Mi az a VPN (virtuális magánhálózat)?
What is a VPN?==

A VPN (virtuális magánhálózat) egy biztonságos kapcsolatot biztosító technológia, amely lehetővé teszi a felhasználók számára, hogy biztonságosan és privát módon kapcsolódjanak hozzáférési pontokhoz a nyilvános interneten keresztül.

A VPN működése a következőképpen zajlik:
1. Titkosítás: Amikor egy felhasználó VPN-kapcsolatot hoz létre, az összes adat, amit küld és fogad, titkosítva lesz. Ez megvédi az adatokat a külső szemek és potenciális támadók ellen.

2. Távoli hozzáférés: A VPN lehetővé teszi a felhasználók számára, hogy távoli hozzáférést szerezzenek egy privát hálózathoz, például egy vállalati hálózathoz vagy otthoni hálózathoz, még akkor is, ha fizikailag nem tartózkodnak az adott helyen.

3. IP-cím elrejtése: Amikor egy felhasználó VPN-t használ, a valódi IP-címe el lesz rejtve, és helyette a VPN-szolgáltató által biztosított IP-címet fogja használni. Ez növeli a felhasználó anonimitását és védelmet nyújt az IP-cím alapú nyomkövetéssel szemben.

4. Hozzáférési korlátozások kikerülése: A VPN segítségével a felhasználók elkerülhetik a földrajzi korlátozásokat és hozzáférhetnek azokhoz az erőforrásokhoz, amelyekhez különben nem lennének jogosultak. Például egy VPN segítségével a felhasználók hozzáférhetnek az országon kívüli tartalmakhoz, amelyekhez egyébként nem lennének jogosultak.

A VPN használata biztosítja az adatbiztonságot és a magánélet védelmét az interneten. Felhasználható személyes és üzleti célokra, valamint a nyilvános Wi-Fi-hálózatokon történő biztonságos böngészésre.


### ==Mi az a DNS (Domain Name System)?
What is DNS?==

A DNS (Domain Name System) egy olyan rendszer, amely a domainneveket fordítja IP-címekké, és lehetővé teszi a számítógépek és az internetes hálózatok számára azonosítani és kommunikálni egymással.

A DNS működése a következő lépésekből áll:
1. Domainnév megadása: Amikor egy felhasználó egy domainnevet (pl. www.example.com) ad meg a böngészőjében, a DNS keresés elindul.

2. DNS kérés elküldése: A felhasználó eszköze elküldi a DNS kérést a DNS-szerverhez, amely felelős a domainnevek feloldásáért.

3. DNS keresés: A DNS-szerverek hierarchikus rendszerben vannak elhelyezve, és a kérés áthalad több szerveren, amíg a megfelelő választ meg nem találja. A szerverek általában a hierarchia alapján dolgoznak, azaz először megkeresik a legfelsőbb szintű (root) DNS-szervereket, majd továbbítják a kérést az adott domainhez tartozó DNS-szervereknek.

4. IP-cím visszaküldése: A megfelelő DNS-szerver megtalálja az adott domainhez tartozó IP-címet, és visszaküldi azt a felhasználó eszközének.

5. Böngészési kérés: Miután az IP-címet kapta, a felhasználó eszköze megkezdi a kapcsolatot a szerverrel, amely a kért weboldalt vagy szolgáltatást tartalmazza. Ez lehetővé teszi a felhasználó számára a tartalom megjelenítését a böngészőben.

A DNS rendszer alapvető fontosságú az internet működéséhez, mivel lehetővé teszi a könnyebb hozzáférést a webhelyekhez a felhasználók számára, mivel nem kell megjegyezniük az IP-címeket. Ehelyett egyszerűen megadhatják a könnyen értelmezhető domainneveket a böngészőjükben, és a DNS segítségével ezek automatikusan lefordulnak az IP-címekre.



### ==Mi az a DHCP (Dynamic Host Configuration Protocol)?
What is DHCP?==

A DHCP (Dynamic Host Configuration Protocol) egy hálózati protokoll, amely automatikusan konfigurálja a hálózati eszközök IP-címét, alhálózati maszkját, alapértelmezett átjáróját és más hálózati beállításait. A DHCP szerver a hálózaton elosztja ezeket a konfigurációs információkat, amelyeket a DHCP kliensek fogadnak és használnak a hálózati kapcsolat felépítéséhez és működéséhez.

A DHCP protokoll használata előnyökkel jár a hálózatkezelés szempontjából, mivel automatizálja az IP-címek, az alhálózati maszkok és az alapértelmezett átjárók kézi beállítását. Ez egyszerűsíti a hálózati konfigurációt és csökkenti a humán hibák lehetőségét. A DHCP lehetővé teszi az IP-címek dinamikus cseréjét, amely hatékonyabbá teszi az IP-címek használatát és optimalizálja a rendelkezésre álló erőforrásokat a hálózaton.

Amikor egy eszköz csatlakozik egy DHCP-képes hálózathoz, a DHCP-kliens elküld egy DHCP kérést a hálózaton található DHCP szerverekhez, amelyek válaszul visszaküldik a konfigurációs információkat. A DHCP-kliens elfogadja ezeket az információkat, konfigurálja a hálózati beállításait, és használatba veszi az elosztott IP-címet és egyéb konfigurációs adatokat a hálózati kommunikációhoz.



### ==Mi az a VPC (Virtual Private Cloud)?
What is a VPC?==

A VPC (Virtual Private Cloud) egy virtuális, izolált hálózati környezet a felhőalapú infrastruktúrában, amely lehetővé teszi az erőforrások elszigetelését és konfigurálását a felhasználói igényeknek megfelelően. Ez a hálózati szolgáltatás lehetővé teszi a felhasználók számára a rugalmas hálózati konfigurációkat, a biztonsági szabályok beállítását és a környezet testreszabását a vállalkozás specifikus igények szerint.




## Security Engineering


### ==Melyik AWS szolgáltatásban tárolható érzékeny adatok?
In what AWS service can you store sensitive data?==

Az AWS (Amazon Web Services) kínál számos szolgáltatást az érzékeny adatok tárolására. 

Az egyik ilyen szolgáltatás az **AWS Secrets Manager**, amely biztonságosan tárolhatja és kezelheti az érzékeny információkat, például jelszavakat, API-kulcsokat, adatbázis-jelszavakat stb. 

Az **AWS Key Management Service (KMS)** pedig lehetővé teszi az adatok titkosítását és kulcskezelését a tárolt adatok védelme érdekében.




### ==Milyen hálózati topológia alkalmas az EC2 elrejtésére?
What network topology is good for hiding EC2?==

Az EC2 (Elastic Compute Cloud) elrejtésére a hálózati topológia szempontjából egy jól alkalmazható megoldás a privát hálózati topológia. Ebben az esetben az EC2 példányokat egy privát alhálózaton helyezik el, amely nem közvetlenül hozzáférhető a nyilvános internetről. A privát hálózati topológia lehetővé teszi az EC2 példányok rejtetten tartását és védelmét a nyilvánosságtól, miközben lehetőséget biztosít a belső hálózati kommunikációra más privát vagy nyilvános alhálózatokkal.




### ==Hogyan nevezik azokat az EC2 példányokat, amelyek egyetlen belépési pontként szolgálnak a védett erőforrásokhoz való hozzáféréshez egy korlátozott hálózaton?
How those EC2 called which are serving as a single entry point for accessing protected resource on a restricted network?==

Azokat az EC2 példányokat, amelyek egyetlen belépési pontként szolgálnak a védett erőforrásokhoz való hozzáféréshez egy korlátozott hálózaton, általában "bastion host"-nak vagy "jump server"-nek nevezik. Ezek a példányok erősítik a hálózati biztonságot, mivel csak rajtuk keresztül lehetséges a bejutás a védett hálózati területekre. A bastion hostok szűrik és irányítják a hálózati forgalmat, és lehetőséget biztosítanak a felhasználók vagy adminisztrátorok számára a biztonságos hozzáférésre és távoli kezelésre a védett erőforrásokhoz.




### ==Melyik AWS szolgáltatás felelős a monitorozásért és a naplógyűjtésért?
What AWS service is responsible for monitoring and log collection?==

Az Amazon CloudWatch egy központosított monitorozási és megfigyelési megoldást biztosít az AWS erőforrásokhoz és alkalmazásokhoz. Számos monitorozási lehetőséget kínál, beleértve a metrikákat, naplókat, eseményeket és irányítópultokat. Íme, hogyan kezeli a CloudWatch a monitorozást és a naplógyűjtést:

1. Metrics (Metrikák):
   - A CloudWatch gyűjti és tárolja a metrikákat, amelyek numerikus adatpontok az AWS erőforrások teljesítményével és viselkedésével kapcsolatban.
   - Különböző AWS szolgáltatásokat és egyedi alkalmazásokat monitorozhat a CPU-használat, a hálózati forgalom vagy a kérési késleltetés stb. metrikák gyűjtésével és elemzésével.
   - A CloudWatch előre elkészített irányítópultokat biztosít, és lehetőséget ad a testreszabott irányítópultok létrehozására a metrikák vizualizálásához és monitorozásához.

2. Logs (Naplók):
   - A CloudWatch Logs lehetővé teszi az AWS erőforrások és alkalmazások naplóinak gyűjtését, monitorozását és tárolását.
   - Valós időben képes naplóadatokat streamelni és tartósan tárolni hosszú távú megőrzés céljából.
   - A naplókat különböző forrásokból rögzítheti, ideértve az EC2 példányokat, a Lambda függvényeket, az AWS szolgáltatásokat és egyedi alkalmazásokat.
   - A CloudWatch Logs központosíthatja a naplógyűjtést, segíthet hibaelhárításban, elemzéseket végezhet, és riasztásokat állíthat be a naplóesemények alapján.

3. Events (Események):
   - A CloudWatch Events eseményvezérelt monitorozást biztosít az AWS erőforrásokhoz és szolgáltatásokhoz.
   - Lehetőséget ad a környezetében történő változásokra és eseményekre történő reagálásra azáltal, hogy kiváltja a műveleteket.
   - Létrehozhat szabályokat a specifikus események megegyezésére, és kiváltást hozhat létre, például EC2 példány indítása, Lambda függvény meghívása vagy értesítés küldése.

4. Alarms and Actions (Riasztások és műveletek):
   - A CloudWatch riasztások lehetővé teszik küszöbértékek beállítását a metrikákon, és műveletek kiváltását, amikor ezek a küszöbértékek megsérülnek.
   - Létrehozhat riasztásokat a specifikus metrikák figyelésére, és automatikus műveleteket hajthat végre, például értesítéseket küldhet, Auto Scalinget indíthat vagy AWS Lambda függvényeket futtathat.

Összefoglalva, az Amazon CloudWatch az AWS szolgáltatás, amely felelős a monitorozásért és a naplógyűjtésért. Széleskörű eszközkészletet kínál metrikák monitorozásához, naplók gyűjtéséhez és elemzéséhez, valamint riasztások és automatikus műveletek beállításához az AWS erőforrásokhoz és alkalmazásokhoz.




### ==Melyik AWS szolgáltatás felelős a tevékenységek nyomon követéséért a fiókon?
What AWS service is responsible for tracking activites on the account?==


Az az AWS szolgáltatás, amely felelős az AWS-fiókon végzett tevékenységek nyomon követéséért, az AWS CloudTrail.

Az AWS CloudTrail egy olyan szolgáltatás, amely lehetővé teszi az AWS-infrastruktúra tevékenységének monitorozását, naplózását és megőrzését. Részletes előzményeket készít az AWS-szolgáltatások felé történő API-hívásokról, és nyomon követi a fiókon belül végrehajtott műveleteket. Az AWS CloudTrail főbb jellemzői és funkcionalitásai a következők:

1. Tevékenység naplózása: A CloudTrail naplózza az AWS-szolgáltatások felé történő API-hívásokat, beleértve az erőforrásokkal kapcsolatos változásokat, a biztonsággal kapcsolatos eseményeket és a kezelési műveleteket. Fontos információkat rögzít, mint például a hívó azonosítója, a hívás időpontja, a forrás IP-címe és így tovább.

2. Fiókszintű naplózás: A CloudTrail nyomon követi a tevékenységet az egész AWS-fiókban, beleértve az összes régiót is. Rögzíti az eseményeket az AWS Management Console, az AWS CLI, az SDK-k és más AWS-szolgáltatások használatával.

3. Eseményelőzmény: A CloudTrail részletes eseményelőzményt biztosít, amelyet keresni és elemzni lehet. Megtekintheti és letöltheti az eseménynaplókat adott időintervallumra, vagy kereséseket hajthat végre konkrét kritériumok alapján.

4. Más szolgáltatásokkal való integráció: A CloudTrail integrálható más AWS-szolgáltatásokkal, például az AWS CloudWatch-val, az AWS S3-mal és az AWS Lambda-val. Konfigurálhatja a CloudTrailt úgy, hogy a naplófájlokat hosszú távú tároláshoz továbbítsa az S3-ba, vagy specifikus események alapján aktiválja a CloudWatch riasztásokat vagy a Lambda függvényeket.

5. Megfelelőség és ellenőrzés: A CloudTrail segít az ellenőrzési és megfelelőségi követelmények teljesítésében. Auditpéldányt nyújt, amelyet biztonsági elemzésre, erőforrás-változás nyomon követésére, hibaelhárításra és megfelelőségi jelentések készítésére lehet használni. Különösen hasznos lehet a PCI DSS, a HIPAA és a GDPR irányelvekkel való megfelelőség igazolásában.

6. Biztonsági elemzés: A CloudTrail naplókat lehet használni biztonsági elemzéshez és monitorozáshoz. Az rögzített API-hívások elemzésével észlelheti a szokatlan tevékenységeket, azonosíthatja a potenciális biztonsági fenyegetéseket és vizsgálhatja az esetleges gyanús magatartásokat.

Összefoglalva, az AWS CloudTrail az a szolgáltatás, amely felelős az AWS-fiók tevékenységeinek nyomon követéséért. Részletes előzményeket készít az AWS-infrastruktúrában végzett API-hívásokról, lehetővé téve az ellenőrzést, a megfelelést, a biztonsági elemzést és a hibaelhárítást.



### ==Mi a különbség az SG (Security Group) és a NACL (Network Access Control List) között?
What is the difference between SG and NACL?==


A Security Group (SG) és a Network Access Control List (NACL) két különböző szintű hálózati biztonsági szolgáltatás az AWS-ben. Itt van néhány különbség közöttük:

1. Hatókör:
   - SG: Az SG-k az AWS szintű tűzfalak, amelyek az EC2 példányok és más AWS erőforrások között működnek. Az SG-k a hálózati forgalmat szűrik a belépő és kilépő irányban az erőforrások között.
   - NACL: A NACL-ek a szintén az AWS-ben működő VPC (Virtual Private Cloud) szintű tűzfalak. A NACL-ek a VPC szintjén irányítják a hálózati forgalmat a kimenő és bejövő irányban.

2. Működési elv:
   - SG: Az SG-k alapvetően stateful tűzfalak, melyek figyelik a kimenő forgalmat, és automatikusan engedélyezik a kapcsolódó választ. Ez azt jelenti, hogy az SG-k megjegyzik a korábbi kommunikációt, és választ adnak a kapcsolódó kérésre.
   - NACL: A NACL-ek stateless tűzfalak, amelyek minden bejövő és kilépő forgalmat külön értékelnek, függetlenül attól, hogy az azonos kapcsolathoz tartozik-e vagy sem.

3. Szabályrendszer:
   - SG: Az SG-k egy sor szabályt tartalmaznak, amelyek megengedik vagy letiltják a hálózati forgalmat az erőforrások között. Az SG-k alapértelmezés szerint zártak, és csak az explicit engedélyezett forgalom engedélyezett.
   - NACL: A NACL-ek egy sor szabályt tartalmaznak, amelyek meghatározzák, hogy milyen hálózati forgalom engedélyezett vagy tiltott a VPC-ben. A NACL-szabályokat az alapértelmezett engedélyezett vagy letiltott forgalomhoz kell hozzáadni.

4. Érvényességi terület:
   - SG: Az SG-k alkalmazhatók az egyes erőforrásokra vagy az erőforrások csoportjára a VPC-n belül. Egy SG-t több erőforrással is megoszthatnak.
   - NACL: A NACL-ek a VPC-szintű tűzfalak, és az összes azonos VPC-ben lévő erőforráshoz alkalmazódnak. Egy NACL csak egy VPC-hoz tartozhat.

Összefoglalva, az SG és a NACL két különböző szintű hálóz

ati biztonsági szolgáltatás az AWS-ben. Az SG-k az AWS erőforrások között működő tűzfalak, míg a NACL-ek a VPC-szintű tűzfalak. Az SG-k stateful működési elvet alkalmaznak, míg a NACL-ek stateless módon dolgoznak. Az SG-k és a NACL-ek különböző szabályrendszerrel és alkalmazási területtel rendelkeznek



#### ==KMS (Key Management Service) és HSM (Hardware Security Module) között mi a különbség?
What is the difference between KMS and HSM?==


KMS (Key Management Service) és HSM (Hardware Security Module) között a következők a főbb különbségek:

1. Funkció:
   - KMS: A KMS egy AWS szolgáltatás, amely kulcsok kezelését és tárolását biztosítja. Ez lehetővé teszi a kulcsok generálását, tárolását, forgalmazását és kezelését az AWS környezetben.
   - HSM: Az HSM egy fizikai eszköz, amely a kulcsok biztonságos tárolását és feldolgozását végzi. Az HSM-k speciális hardverek, amelyek a kulcsokat kriptográfiai műveletek elvégzésére használják, és a fizikai biztonságuk magas szintjét biztosítják.

2. Hozzáférési mód:
   - KMS: A KMS felhőalapú szolgáltatás, amelyhez hálózati kapcsolaton keresztül lehet hozzáférni az AWS konzolon, API-kon, vagy CLI-n keresztül.
   - HSM: Az HSM fizikai eszköz, amelyet az ügyfél saját infrastruktúrájában kell telepíteni és kezelni. Az HSM-hez való hozzáférés általában közvetlenül a helyi hálózaton vagy dedikált kapcsolaton keresztül történik.

3. Rugalmasság és skálázhatóság:
   - KMS: A KMS skálázható és rugalmas szolgáltatás az AWS környezetben. Könnyen lehet új kulcsokat létrehozni, kezelni és forgalmazni a KMS API-k segítségével.
   - HSM: Az HSM-ek hardveralapú eszközök, amelyeknek korlátozott kapacitása és skálázhatósága van. Az új HSM-ek telepítése és konfigurálása időigényes folyamat lehet.

4. Biztonság:
   - KMS: A KMS a kulcsokat végpontokon tárolja, amelyeket biztonságosan kezel az AWS infrastruktúrájában. Az AWS biztonsági intézkedései és a kulcsok automatikus forgalmazása biztosítja a magas szintű biztonságot.
   - HSM: Az HSM-ek fizikai eszközök, amelyeket speciális biztonsági intézkedésekkel védnek. Az HSM-ek segítségével a kulcsokat kizárólag a HSM-ben lehet tárolni és feldolgozni, így magasabb biztonsági szintet biztosítanak.

Összességében a KMS egy felhőalapú szolgáltatás, amelyet az AWS környezetben használnak, míg az HSM egy fizikai eszköz, amelyet az ügyfelek saját infrastruktúrájában telepítenek. Mindkét megoldás biztonságos kulcskezelést tesz lehetővé, de eltérő működési és hozzáférési jellemzőkkel rendelkeznek.




## Application

### ==Mi a különbség a Docker és a virtuális gép (Virtual Machine) között?
What is the difference between Docker and Virtual Machine?


1. Virtual Machine (VM):
   - Egy VM egy teljes operációs rendszert és annak szükséges erőforrásait emulálja egy fizikai gépen.
   - A VM-hez szükség van egy virtualizációs rétegre, amely a hardver erőforrásokat (processzor, memória, tárhely stb.) felosztja a virtuális gépek között.
   - Minden VM külön operációs rendszert futtat, és szigorúan elkülönül egymástól.

2. Docker:
   - A Docker konténerizációt használja, amely könnyűsúlyú, gyors és hatékony módja az alkalmazások futtatásának.
   - A Docker konténer egy izolált futtatókörnyezetet biztosít az alkalmazásnak, amelyben az alkalmazás és annak függőségei futnak.
   - A konténerek megosztják a rendszer erőforrásait (operációs rendszer kerneljét), de elkülönülnek egymástól.
   - Az alkalmazásokat konténerekbe csomagolják, amelyek hordozhatóak és könnyen skálázhatóak.

A legfőbb különbség tehát az, hogy a virtuális gép egy teljes operációs rendszert emulál, míg a Docker konténereken belül az alkalmazások futnak, és megosztják az operációs rendszer erőforrásait. Ezáltal a Docker könnyebb, gyorsabb és hatékonyabb megoldást nyújt az alkalmazások futtatására és skálázására.



### ==A Dockerfile alap képének meghatározásához milyen kulcsszót használunk?
What is the keyworld for defining the base image of a Dockerfile?

A Dockerfile-ban az alap kép (base image) meghatározásához a `FROM` kulcsszót használjuk. Ez a kulcsszó jelzi, hogy melyik alap képből építsük fel a Docker konténerünket.

Multistage Dockerfile build: 
2 FROM használatával,  ezzel le lehet redukálni a image méretét.

```dockerfile
Build Stage 1
This build created a staging docker image 
FROM node:10.15.2-alpine AS appbuild
WORKDIR /usr/src/app 
COPY package.json ./ 
COPY .babelrc ./ 
RUN npm install COPY ./src ./src 
RUN npm run build

Build Stage 2 
This build takes the production build from staging build 
FROM node:10.15.2-alpine 
WORKDIR /usr/src/app 
COPY package.json ./ 
COPY .babelrc ./ 
RUN npm install 
COPY --from=appbuild /usr/src/app/dist ./dist 
EXPOSE 4002
CMD npm start [4:55 PM] 
COPY --from=appbuild /usr/src/app/dist ./dist
```



### ==`CMD` és `ENTRYPOINT` között mi a különbség?
What is the difference between CMD and ENTRYPOINT?==

A Docker konténerekben használt `CMD` és `ENTRYPOINT` utasítások különböző módon határozzák meg a konténer alapértelmezett futtatási parancsát.

- `CMD`: Az `CMD` utasítás meghatározza a konténerben futtatandó parancsot vagy parancssort. Ha a Dockerfile-ban csak egy `CMD` utasítás található, akkor az a konténer alapértelmezett parancsa lesz. Ha a Docker parancssorában vagy a `docker run` parancsban megadunk egy másik parancsot, akkor az felülírja az `CMD` által meghatározott parancsot.

- `ENTRYPOINT`: Az `ENTRYPOINT` utasítás meghatározza a konténer alapértelmezett futtatható fájlt vagy parancsot. Az `ENTRYPOINT` és az opcionális `CMD` utasítás együtt határozza meg a konténer futtatásakor végrehajtandó parancsot. Az `ENTRYPOINT` által meghatározott parancshoz a Docker parancssorában vagy a `docker run` parancsban megadott argumentumokat hozzá lehet adni.

A különbség tehát az, hogy az `ENTRYPOINT` utasítás által meghatározott parancs mindig végrehajtódik a konténer futtatásakor, míg a `CMD` utasítás által meghatározott parancs felülírható a Docker parancssorában vagy a `docker run` parancsban megadott másik parancs által.




### ==Milyen a szerkezete egy minimális Kubernetes telepítésnek?
What is the layout of a minimal Kubernetes deployment?==

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: minimal-pod
spec:
  containers:
  - name: my-container
    image: nginx:latest
    ports:
    - containerPort: 80
```

Ez a YAML fájl egyetlen Podot definiál, amelyben egyetlen konténer található. A konténer egy `nginx` képből indul el, és a `80` portot nyitja meg. A fájlt létrehozhatod és alkalmazhatod a `kubectl` parancs segítségével a Kubernetes klaszteren, illetve ha updatelni szeretnénk akkor is a következő a parancs sor :

```bash
kubectl apply -f minimal-pod.yaml
```

Ezután a Kubernetes elindítja a Podot a megadott konténerrel a klaszteren.

apiVersion: podok tudjanak egymással kommunikálni  
KIND:  depolyment, service, statefulset, ingress(API object: deployolni kell egy controllert emellé (pl.: NGINX, FLASK, NODEJS))  
METADATA:  
NAME: mi lesz a neve, ez UID  
LABEL: Podok egymás közt labeleken kommunikálnak  
SPEC:




### ==Mi a különbség a Deployment és a StatefulSet Kubernetes objektumok között?
What is the difference between Deployment and StatefulSet kubernetes object?==


A Deployment és a StatefulSet Kubernetes objektum között az alábbiakban található különbségek:

1. Skálázás és replikáció: 
	1. A Deployment lehetővé teszi a horizontális skálázást és a replikáció kezelését. Ez azt jelenti, hogy könnyedén növelhető vagy csökkenthető a podok száma a replikák létrehozásával vagy megszüntetésével. 
	2. A StatefulSet viszont olyan alkalmazásokhoz használatos, ahol a podoknak egyedi, állandó neve és állapota van. A StatefulSet nem támogatja a horizontális skálázást, és az egyes podokat egyenként kell kezelni.

2. Egyediség és szekvenciális indítás: 
	1. A StatefulSet lehetővé teszi az egyedi névvel rendelkező podok létrehozását, amelyekhez állandóan tartozik egy index (pl. pod-0, pod-1 stb.). Ez lehetővé teszi a podok számára, hogy megtartsák az egyedi állapotukat és azonosíthatóak legyenek. 
	2. A Deployment nem garantálja az egyediséget vagy a szekvenciális indítást, és a podokat dinamikusan hozza létre vagy szünteti meg.

3. Adatmegőrzés: 
	1. A StatefulSet lehetővé teszi az adatoknak való hozzáférést és tárolást a podok életciklusa között. Ezáltal az alkalmazásoknak lehetőségük van az adatok tartós tárolására és visszaállítására, például adatbázisok vagy következetes állapotot igénylő szolgáltatások esetén. 
	2. A Deployment nem biztosít adatmegőrzési mechanizmust.

Összefoglalva, a Deployment és a StatefulSet különböző kubernetes objektumok, amelyek különböző célokat szolgálnak. A Deployment inkább alkalmazható skálázható és replikálható alkalmazásokhoz, míg a StatefulSet olyan alkalmazásokhoz ajánlott, amelyeknek szükségük van egyedi névre és állapotra, valamint adatmegőrzési lehetőségre a podok között.



### ==Miért felel a Kubernetes Service Objectum
What is a Service kubernetes object responsible for?==

A kliensek és a mögöttes podok közötti kapcsolatot és kommunikációt kezeli. Biztosítja a hálózati felfedezést, terheléselosztást, skálázhatóságot, rugalmasságot és DNS névrendszert az alkalmazások számára.



### ==Hogyan érhető el egy Kubernetes pod a nyilvános internetről?
How can be a kubernetes pod reached from the public internet?==

A Kubernetes podok alapértelmezetten nem érhetők el közvetlenül a nyilvános internetről. Azonban a következő lehetőségek állnak rendelkezésre a Kubernetes podok elérésére a nyilvános internetről:

1. Load Balancer (Terheléselosztó): Egy klaszter szintű terheléselosztó beállítása lehetővé teszi a Kubernetes podok elérését a nyilvános internetről. Az egyes podok mögötti terhelést a terheléselosztó automatikusan kezeli, így a kérések egyenletesen oszlanak meg a podok között.
    
2. Ingress Controller: Az Ingress Controller egy kiterjesztés a Kubernetes rendszerben, amely lehetővé teszi a bejövő forgalom irányítását és a podok elérését a nyilvános internetről. Az Ingress Controller használatával definiálhatunk útvonalakat és szabályokat, hogy irányítsuk a bejövő forgalmat a megfelelő podokhoz.
    
3. NodePort: A NodePort beállítás lehetővé teszi a podok elérését a nyilvános interneten a Kubernetes klaszter node-jain keresztül. Egy kiválasztott portot rendelhetünk a podokhoz, és a klaszter node-jainak ezen a porton keresztül lehet elérni a podokat.
    

Fontos megjegyezni, hogy az elérhetőség konkrét módszere a Kubernetes környezettől, a klaszter konfigurációjától és a választott felhőszolgáltatótól függ. Az elérési módokat és beállításokat a környezet specifikációja határozza meg.




### ==Mi a különbség a LivenessProbe és a ReadinessProbe között?
What is the difference between LivenessProbe and ReadinessProbe?==

A LivenessProbe ellenőrzi, hogy a konténer él és fut. A ReadinessProbe ellenőrzi, hogy a konténer kész-e fogadni a forgalmat. Mindkét probe segít biztosítani az alkalmazások elérhetőségét és megbízhatóságát azáltal, hogy monitorozzák azok egészségi állapotát, és a probe eredményeinek megfelelő intézkedéseket tesznek.




### ==Mi a különbség a erőforrás Limit és Request között?
What is the difference between resource Limit and Request?==

- Erőforrás Limit: Ez meghatározza az erőforrások maximális mennyiségét, amelyet egy konténer használhat. Ez az érték biztosítja, hogy a konténer ne haladja meg a rendelkezésre álló erőforrások határát. Például a CPU és memória Limit határozza meg, hogy egy konténer mennyi processzoridőt és memóriát használhat.

- Erőforrás Request: Ez meghatározza az erőforrások minimális mennyiségét, amelyet egy konténer kér az induláskor. Ez az érték segít a Kubernetes rendszernek kiszámítani és fenntartani az erőforrások megfelelő elosztását a konténerek között. Például egy CPU és memória Request meghatározza, hogy egy konténernek mennyi erőforrásra van szüksége a futtatáshoz.

A Limit és Request beállítások lehetővé teszik a Kubernetes rendszer számára az erőforrások hatékony kezelését és a konténerek megbízható működését a rendelkezésre álló erőforrások keretein belül.




## Infrastructure as Code

### ==Milyen alap parancsok vannak a Terraform CLI-ben?
What are the basic commands of the terraform cli?==


`terraform init`: Inicializálja a Terraform munkakönyvtárát a konfigurációs fájlokban megadott szolgáltatói pluginok és modulok letöltésével és konfigurálásával. Ez a parancs általában egyszer fut le egy új Terraform projektben vagy ha megváltoznak a konfiguráció függőségei.

`terraform plan:` Létrehoz egy végrehajtási tervet a jelenlegi konfigurációs fájlok elemzésével és azok összehasonlításával a meglévő infrastruktúrával. Megjeleníti a tervezett változtatásokat, amelyeket alkalmazni fog a terraform apply végrehajtásakor. A plan parancs segít megérteni a változtatások hatását, mielőtt ténylegesen módosítanád az erőforrásokat.

`terraform apply`: Alkalmazza a Terraform konfigurációs fájlokban meghatározott változtatásokat az erőforrások létrehozásához, frissítéséhez vagy törléséhez. Módosítások végrehajtása előtt megerősítést kér. Az apply parancs segítségével hajtod végre a terraform plan által leírt terveket.

`terraform destroy`: Megsemmisíti a Terraform konfigurációval kezelt összes erőforrást, az infrastruktúra teljes törlését eredményezi. Megsemmisítés előtt megerősítést kér. Ez véglegesen törli az erőforrásokat.

`terraform validate`: Ellenőrzi a Terraform konfigurációs fájlok szintaxisát és struktúráját anélkül, hogy végrehajtana vagy módosítana bármilyen erőforrást. Ellenőrzi a hibákat, helyesírási hibákat és egyéb problémákat a konfigurációs fájlokban.

`terraform state`: Különböző alparancsokat biztosít a Terraform állapotfájl kezeléséhez, amely nyomon követi a kezelt erőforrások állapotát. Ezzel a paranccsal megtekintheted, módosíthatod, importálhatod és kezelheted az erőforrásállapotokat közvetlenül.

`terraform output`: Megjeleníti a Terraform konfigurációs fájlokban meghatározott kimeneti értékeket. Ezek a kimenetek információkat tartalmazhatnak, például erőforrásazonosítókat, IP-címeket vagy más, az infrastruktúrából származó értékeket.




### ==Mi a különbség a data és a resource között Terraformban?
What is the difference between resource and data in terraform?==

A Terraformban a "resource" és a "data" két különböző típusú konstrukció, amelyek segítenek az infrastruktúra kezelésében. 

Resource (erőforrás):
- Az erőforrások azok a Terraform objektumok, amelyeket a konfigurációs fájlokban definiálhatsz, és amelyek létrehozzák, frissítik vagy törlik az infrastruktúrát.
- Az erőforrások általában a cloud szolgáltató (pl. AWS, Azure) specifikus erőforrásokat reprezentálják, például virtuális gépek, adatbázisok vagy hálózati erőforrások.
- Az erőforrásokat használhatod az infrastruktúra létrehozására és kezelésére, és Terraform segítségével biztosítja az állapot nyomon követését és a változtatások menedzselését.

Data (adat):
- Az adatok lehetővé teszik az adatok lekérdezését és használatát a konfigurációs fájlokban anélkül, hogy létrehoznának vagy módosítanának bármilyen erőforrást.
- Az adatok lehetővé teszik az infrastruktúrával kapcsolatos információk megszerzését és felhasználását, például erőforrások tulajdonságainak lekérdezését vagy külső adatforrásokból történő adatlekérdezést.
- Az adatok segítségével validálhatod vagy paraméterezheted a konfigurációs fájlokat, és dinamikusan beállíthatod az erőforrások tulajdonságait.

Összefoglalva, a "resource" az infrastruktúra létrehozására és kezelésére szolgál, míg a "data" adatok lekérdezését és felhasználását teszi lehetővé a konfigurációs fájlokban, anélkül hogy létrehozná vagy módosítaná az erőforrásokat.



### ==Mi az a state a terraform kontextusában?
What is state in the context of terraform?==

A Terraform az állapotfájlt használja annak nyomon követésére, hogy milyen erőforrások vannak létrehozva, módosítva vagy törölve az infrastruktúrában. Az állapotfájl tárolja az aktuális konfiguráció és az aktuális infrastruktúra közötti különbségeket, és ez alapján hozza létre, frissíti vagy törli az erőforrásokat.

Az állapotfájl tartalmazza az erőforrásokat, azok attribútumait és a hozzájuk tartozó metadatákat. Ez az állapotfájl biztosítja a Terraform számára az infrastruktúra kezeléséhez szükséges információkat, például az erőforrások azonosítóit, az erőforrások közötti függőségeket és az előzőleg végrehajtott módosításokat.

Az állapotfájl fontos része a Terraform működésének és az infrastruktúra biztonságos és konzisztens kezelésének. Az állapotfájlt általában tárolórendszerekben, például AWS S3 vagy más tárolószolgáltatásokban tárolják, hogy megőrizzék az állapot integritását és hozzáférhetőségét a csapat tagjai számára.

Összefoglalva, az "állapot" a Terraformban az infrastruktúra aktuális állapotát jelöli, és az állapotfájlban tárolódik, amely tartalmazza az erőforrásokat, attribútumokat és metadatákat.

