# korduva-kryptogrammi-juhtum

Mis juhtus e-häälte auditeerimisel 2025. aasta KOV valimistel? Audiitori 20.10.2025 toimingu käigus leidis aset segadus, mille asjaolud vaikib audiitor maha ka [oma 22.12.2025 lõpparuandes](https://www.valimised.ee/sites/default/files/2025-12/L%C3%B5pparuanne%20KOV2025%20e-h%C3%A4%C3%A4letuse%20audit%2022.12%201.asice).

Esialgse kokkuvõtte toimunust leiab [3.11.2025 blogipostitusest](https://gafgaf.infoaed.ee/posts/korduva-kryptogrammi-juhtum/), mille kohta on ka [kokkuvõttev video](https://youtu.be/clmqgo9b6dY).

Tegu on osalise korduslugemisega tegelike KOV valimistel antud häältega, mille valijad salvestasid hääletusprotsessi käigus. Vaidlusi põhjustasid _korduvad krüptogrammid_, mida audiitori raporti väitel oli viis ja mida audiitor oma raportis ekslikult samastab töötlemisrakenduse tuvastataud viie mitte-unikaalse registreerimisteenuse päringu andnud häälekonteineriga:

```
E-valimiskasti laadimine failist 'conf/../votes.zip'
E-valimiskast on laaditud
E-valimiskasti liigi kontrollimine
E-valimiskasti liik on "Korrastamata e-valimiskast"
Kogumisteenus andis e-valimiskasti koosseisus üle 14 häält
E-valimiskasti andmetervikluse kontrollimine
100% [..................................................] 14 / 14
E-valimiskastis sisalduvad andmed on terviklikud
E-valimiskastis on 14 kvalifitseerimiseks sobivat häält
E-valimiskastis sisalduvate häälte digiallkirja vormingule vastavuse kontrollimine
 92% [..............................................    ] 13 / 14
Viga valija *******2724 hääle **************366+0300 töötlemisel: Registreerimispäringu vastus pole unikaalne
100% [..................................................] 14 / 14
Viga valija *******2724 hääle **************407+0300 töötlemisel: Registreerimispäringu vastus pole unikaalne
Viga valija *******2724 hääle **************718+0300 töötlemisel: Registreerimispäringu vastus pole unikaalne
Viga valija *******2724 hääle **************724+0300 töötlemisel: Registreerimispäringu vastus pole unikaalne
Viga valija *******2724 hääle **************766+0300 töötlemisel: Registreerimispäringu vastus pole unikaalne
100% [..................................................] 14 / 14
E-valimiskastis sisalduvate häälte koguarv: 14
E-valimiskastis sisalduvate korrektse allkirjaga häälte arv: 9
E-valimiskastis sisalduvate vigase allkirjaga häälte arv: 5
```

Kuna hiljem kuvas auditirakendus audiitorile teadet viiest korduvast krüptogrammist, siis audiitor paistab olevat viis identset häälekonteinerit ja viis korduvat krüptogrammi ekslikult samastanud:

```
E-valimiskasti laadimine failist 'conf/../votes.zip'
E-valimiskast laaditud
 
Anonüümitud e-valimiskasti laadimine failist 'conf/../out-4/KOV_2025-bb-4.json'
Anonüümitud e-hääled laaditud

E-valimiskasti verifitseerimise logifail: conf/../out-2/KOV_2025.question-KOV_2025.check.log1
Korduvhäälte tühistamise logifail: conf/../out-2/KOV_2025.question-KOV_2025.squash.log2
Topelthäälte tühistamise logifail: conf/../out-4/KOV_2025.question-KOV_2025.revoke.log2
E-häälte anonüümimise logifail: conf/../out-4/KOV_2025.question-KOV_2025.anonymize.log3
E-valimiskasti töötlemisvigade raport: conf/../out-2/ballotbox_errors.txt
 
Vastuvõetud häälte seas on korduvaid krüptogramme

There are 5 ciphertext recurrences among the accepted ballots
Recurring ballot: G6kFbO2dR2GFRfQ1PgVBDXp652p8M0+NRC4o1Dnk3gk=
Recurring ballot: 9WhZ6IFiaA8Hhw8/vrHBhvY9+VwGz89olrW02YrRvUQ=
 
Ballot '47608082724/20251015055435718+0300' present in both the acceptance and rejection logs
Ballot '47608082724/20251015055435288+0300' not found in the acceptance/rejection logs

E-valimiskasti verifitseerimise logid on terviklikud: ei
 
Auditirakendus lõpetas töö ilma vigadeta
```

Korduslugemine annab tulemuseks, et korduvaid krüptogramme oli valimiskastis vähemalt 13, mille hulgas olid:

1. Kuus identset häälekonteinerit, mis sisaldavad ka identseid krüptogramme, millest häiret anti _viie viimase puhul_;
2. Seitse unikaalset häälekonteinerit, millest viis sisaldasid ühte identset krüptogrammi ja kaks teist identset krüptogrammi, millest kummagi puhul anti häiret viimaste puhul, st 5-1 = 4 ja 2-1 = 1 ehk kokku samuti _viie korduva krüptogrammi puhul_.

Audiitor küll märgib korrektselt, et "töötlemisrakendus tuvastas viis häält, millel oli määrang `Registreerimisteenuse päring pole unikaalne`", kuid samastab ekslikult need identsete häälekonteinerite kohta antud teated korduvate krüptogrammide kohta antud teavitusega, mida oli samuti viis. Siiski puudub _viiel identsel häälekonteineril_ ja _viiel korduval krüptogrammil_ omavaheline seos töötemis- või auditirakenduse kontekstis ja tegu on täiesti isoleeritud juhtumitega.

Seejuures käivad määrangud `present in both the acceptance and rejection logs` ja `not found in the acceptance/rejection logs` viie töötlusfaasis tuvastatud identse häälekonteineri kohta ja `there are 5 ciphertext recurrences among the accepted ballots` viie auditirakenduse jooksutamise käigus ilmnenud korduva krüptogrammi kohta.

Seetõttu on vale audiitori väide, et "töötlemisrakendus tuvastas viis häält, millel oli määrang `Registreerimisteenuse päring pole unikaalne`" ja "vea andis audiitorrakendus, kuna selle algoritm ei sisalda kasutusjuhtu, kui isetehtud valijarakendusega saadetakse kogujasse üks ja sama krüptogramm korduvalt".

Auditirakenduse eksplitsiitselt arvestas nii korduvate krüptogrammide kui identsete häälekonteineritega, mille kohta võib leida märkuse [lähtekoodi kommentaaridest](https://github.com/valimised/ivxv/blob/v1.10.4-KOV2025/auditor/src/main/java/ee/ivxv/audit/tools/IntegrityTool.java#L239-L243):

```
// We must use a bag instead of a set since it might happen (statistically unlikely unless intentional)
// that there are ballots with the same ciphertext. Therefore, a set would not correctly represent the
// state of the accepted ballots.
```

Ka auditirakenduse tegelikul jooksutamisel arvestas algoritm korrektselt just nimelt korduvate krüptogrammidega: viie korduva krüptogrammi olemasolu valimiskastis ega selle kohta antud teade auditirakenduse käitamisel probleeme ei tekitanud.

Küll aga tekitas probleeme identsete häälekonteinerite töötlemisel auditirakenduses esinev programmeerimisviga, mille raames ühildati valesti funktsiooni `getValidInvalidSums` parameetritena edasi antud `set` ja `list` andmetüüpe.

Selle tõttu eemaldati [IngegrityTooli ridadel 268-278](https://github.com/valimised/ivxv/blob/v1.10.4-KOV2025/auditor/src/main/java/ee/ivxv/audit/tools/IntegrityTool.java#L268-L278) esimese identse häälekonteinerini jõudes ühekorraga kõik identsed häälekonteinerid, mille tõttu esimesel läbimisel kuvati teadet `present in both the acceptance and rejection logs` ja teisel läbimisel `not found in the acceptance/rejection logs`, sest konteineri räsi enam massiivist ei leitud.

Audiitori poolt väidetud korduvate krüptogrammide töötlemisega mitte arvestamine algoritmi tasemel oli hoopis lihtne identsete häälekonteinerite töötlemise programmeerimisviga, mis oli jäänud koodi sisse sõltumata sellest, et programmeerija oli endale kirjutanud eraldi märkuse sellest veast hoidumise vajaduse kohta.

Ka polnud viga tulnud välja testimise käigus ega 2024. aasta Euroopa Parlamendi valimistel, kus sama auditirakenduse kood samuti kasutusel oli.

Kuna audiitor toimingute raames luges kokku rohkem kui kümme korduvat krüptogrammi, aga aruandes piirdub viie korduva krüptogrammi nimetamisega ning ei anna adekvaatset hinnangut intsidendi põhjustele, siis võib oletada, et korduvate krüptogrammide juhtumi asjaolude varjamise põhjuseks pole üksnes audiitori tehniliste teadmiste piiratus.

Kui tahad ise sammud läbi teha, siis:

```
rm -r out-*
rm -r log

./processor checkAndSquash -c conf/certs.asice -p conf/processor.asice
digidoc-tool create --file=out-2/KOV_2025-bb-2.json.sha256sum out-2/KOV_2025-bb-2.json.sha256sum.asice
./processor revokeAndAnonymize -c conf/certs.asice -p conf/processor.asice
./auditor integrity -c conf/certs.asice -p conf/auditor.asice
```

Töötlemisrakenduse ja auditirakenduse töölesaamiseks eelnevalt:

```
git clone --recurse-submodules https://github.com/infoaed/korduva-kryptogrammi-juhtum.git
cd korduva-kryptogrammi-juhtum
git submodule update --init --recursive

sudo apt update
sudo apt install -y openjdk-21-jdk

wget https://services.gradle.org/distributions/gradle-8.11-bin.zip
unzip gradle-8.11-bin.zip -d ivxv/common/external
rm gradle-8.11-bin.zip

cd ivxv
common/external/gradle-8.11/bin/gradle -p ivxv/processor clean build installDist -g=ivxv/common/external/java --refresh-dependencies
make processor
make auditor

cd ..
```
