# Git

## Enkonduko al Git

### Priskribo de Versikontrolo

Versikontrolo estas esenca ilo en la mondo de programaj kreiĝo, agante kiel speco de "tempa maŝino" por kodo. Ĝi permesas al programistoj sekvadi kaj administri ŝanĝojn en ilia fontkodo dum la tempo. Tio estas kritika por kompreni la evoluon de programprojekto, ebligante plurajn homojn labori sur la sama koda bazo sen interferado.

Ekzistas du ĉefaj tipoj de versikontrolsistemoj: centraligitaj kaj distribuitaj. Centraligita versikontro, kiel Subversion (SVN), ĉirkaŭiras ĉirkaŭ unu centran servilon kiu stokas ĉiujn versiojn de projekto, dum distribuitaj versikontrolsistemoj, kiel Git, permesas al ĉiu uzanto havi kompleta kopion de la tuta projekthistorio, ebligante pli fleksajn kaj rezistantajn laborfluojn.

### La Signifo de Git en Moderna Programa Evoluo

Git, kreita de Linus Torvalds en 2005 por la evoluo de la Linukso kernelo, estas la plej larĝe uzata distribuita versikontrolsistemo hodiaŭ. Ĝia signifo en moderna programa evoluo ne povas esti trosubigita pro pluraj kialoj:

1. **Distribuita Naturo**: Kontraste al centraligitaj sistemoj, Git donas al ĉiu programisto lokan kopion de la tuta projekthistorio, plibonigante rapidon kaj ebligante laboron eĉ sen konekto al retumo.

2. **Branĉado kaj Kunfandado**: La potencaj branĉado kaj kunfandado kapabloj de Git igas ĝin ideala por eksperimentado kun novaj trajtoj kaj administri diversajn programado-stadiojn. Tio ebligas pli agilan kaj fleksan evoluoproceson.

3. **Kunlaborado kaj Malferma Kodo**: Git estas integra al platformoj kiel GitHub, GitLab, kaj Bitbucket, kiuj faciligas kunlaborkodigon. Tio signife propelis la malferma-kodan movadon, ebligante programistojn de tutmonde facile dividi kaj kunlabori pri projektoj.

4. **DevOps kaj Daŭriga Integrado/Daŭriga Publikigo (CI/CD)**: Git senprobleme integriĝas kun multaj CI/CD kaj DevOps iloj, fariĝante fundamenta en tiuj praktikoj, kiuj estas centraj al moderna programa livero.

### Baza Koncepcioj: Deponejo, Kontribuo, Branĉo

- **Deponejo**: Git deponejo (aŭ repo) estas la koro de la versikontrolsistemo de Git. Ĝi estas la enhavo de via projekta kodo kaj ĝia historio. Esence, ĝi estas dosierujo kiu enhavas ĉiujn dosierojn rilatajn al via projekto kaj specialan dosierujon `.git` kiu stokas la metadatumojn kaj objektan datumbazon de via projekto. Deponejoj povas esti klonitaj, ebligante uzantojn havi sian propran kompletan version de la projekto.

- **Kontribuo**: Kontribuo en Git estas momenta preno de via projekta dosieroj je specifa tempo. Ĝi reprezentas la kulminon de serio da ŝanĝoj kaj estas identigita per unika SHA-1 cifero. Ĉiu kontribuo registritas la projekthistorion kaj inkluzivas informojn kiel la aŭtoron, daton, kaj kontribua mesaĝo priskribanta la ŝanĝojn.

- **Branĉo**: Branĉoj en Git estas montriloj al kontribuoj kaj reprezentas sendependan evoluolinion en projekto. La defaŭlta branĉo en Git estas `master` (lastatempe renomita al `main` en multaj platformoj). Branĉoj ebligas diverĝi de la ĉefa evoluolinio por labori pri novaj trajtoj aŭ riparoj sen influo al la ĉefa kodo. Unufoje ke la evoluado en branĉo estas kompleta, ĝi povas esti kunfandita reen en la ĉefa branĉo.

Kompreni ĉi tiujn koncepcojn estas la unua paŝo al mastrumado de Git, ilo kiu fariĝis necesa en la pejzaĝo de moderna programa evoluo. Ĉu vi estas solema programisto aŭ parto de granda teamo, lerni Git malfermas la pordon al pli efika, kunlabora, kaj kontrolita programa evoluo.

## Konfigurado de Git

### Instalado de Git sur Diversaj Operaciumoj

Git estas versatila kaj povas esti instalita sur la plejmulto de operaciumoj. Jen kiel instali Git-on sur la ĉefaj platformoj:

#### Windows
1. **Elŝutu la instalilon de Git**: Vizitu la oficialan retejon de Git ([git-scm.com](https://git-scm.com/)) kaj elŝutu la lastan version de Git por Windows.
2. **Rulu la instalilon**: Sekvu la instalkapablajn paŝojn, elektante defaŭltajn opciojn aŭ aliformigante laŭ bezono. La instalilo inkluzivas Git Bash (komandlinia aplikaĵo) kaj la eblecon elekti Git GUI.

#### macOS
1. **Metodo kun Homebrew**: Se vi havas Homebrew instalitan (populara pakaĵadministrilo por macOS), simple malfermu la Terminalon kaj rulu `brew install git`.
2. **Instalilo-pakaĵo**: Vi ankaŭ povas elŝuti la macOS-instalilon de Git de la oficiala retejo de Git. Rulu la pakaĵon kaj sekvu la instalajn instrukciojn.

#### Linux
Por Linux, la instalada proceso iom varias depende de la distribuo:

- **Debian/Ubuntu**: Uzu `sudo apt-get install git`
- **Fedora**: Uzu `sudo dnf install git`
- **Aliaj distribuoj**: Uzu la respektivan pakaĵadministrilon aŭ kompilu Git-on el la fonto.

### Konfigurado de Git: Agordado de Uzantnomo kaj Retadreso

Post instali Git-on, vi devas agordi vian uzantnomon kaj retadreson, ĉar Git enmetis tiun informon en ĉiun kontribuon. Tio estas vitale por kunlabora laboro. Jen kiel fari tion:

1. **Malfermu la Komandlinion**: Malfermu vian komandolinian aplikaĵon (Terminalon sur macOS kaj Linux, Git Bash sur Windows).
2. **Agordu Vian Uzantnomon**: Rulu `git config --global user.name "Via Nomo"`.
3. **Agordu Vian Retadreson**: Rulu `git config --global user.email "via_retadreso@example.com"`.

Tiaj komandoj agordas vian nomon kaj retadreson ĉie globalaj en ĉiuj viaj Git-deponejoj. Se vi bezonas agordi malsamajn kredencialojn por specifa projekto, vi povas ruli tiujn komandojn sen la `--global` flago en tiu projekta dosierujo.

### Enkonduko al Git GUI-klientoj kaj IDE-Integriĝoj

Kvankam Git ofte uzatas tra la komandlinio, estas pluraj grafikaj uzantinterfacoj (GUI) kaj integriĝoj al Integrita Evoluo-Programo (IDE) kiuj igas ĝin pli alirebla kaj facile uzebla, precipe por tiuj nekomfortaj kun komandliniaj iloj.

#### Git GUI-klientoj
- **GitKraken kaj SourceTree**: Tio estas popularaj Git GUI-klientoj kiuj proponas bildan reprezentadon de viaj deponejoj. Ili provizas uzantamikan interfason por kompleksaj Git-komandoj kiel branĉa administrado, kunfandado, kaj pli.
- **GitHub Desktop**: Tiu estas simpla GUI-ililo provizita de GitHub, kiu taŭgas por komencantoj kaj integriĝas senproblemere kun GitHub-deponejoj.

#### IDE-Integriĝoj
- **Visual Studio Code, IntelliJ IDEA, kaj Eclipse**: La plej modernaj IDE-oj havas enkonstruitan subtenon por Git. Tiaj integriĝoj permesas al vi efektivigi Git-operaciojn rekte el via IDE, igante la evoluopronon pli fluanta kaj integrita.

Ĉu vi preferas uzi la komandlinion, GUI-on aŭ IDE-on por viaj Git-operacioj, la varieco de iloj disponeblaj igas Git-on tre adaptebla kaj potenca versikontrolsistemo por ĉiaj specoj de evoluofluoj.

## Kreante Vian Unuan Deponejon

Krei vian unuan Git-deponejon estas simpla procezo kiu starigas la fundamentojn por versikontrolo en via projekto. Jen kiel vi povas fari tion, kune kun kompreno de la `.git` dosierujo kaj kiel stadi kaj kontribui vian unuan dosieron.

### Inicialigante Novan Git-Deponejon

1. **Kreu novan dosierujon por via projekto** (se vi ankoraŭ ne faris tion). Vi povas fari tion uzante vian dosiersistemon aŭ rulante `mkdir via-projektnomo` en la komandlinio.
2. **Navigu en vian projektdosierujon**. Uzu la komandon `cd via-projektnomo` por moviĝi en vian novan projektdosierujon.
3. **Inicialigu la deponejon**. Rulu `git init`. Tiu komando kreas novan subdosierujon nomitan `.git`, kiu enhavas la internan datan strukturon necesan por versikontrolo. Post tiu paŝo, via projekto nun estas Git-deponejo.

### Komprenado de la Dosierujo .git

- La dosierujo `.git` estas kie Git stokas la metadatumojn kaj objektdatan datumbazon por via projekto. Ĝi estas la plej grava parto de Git, kaj ĝi estas kio transformas dosierujon en Git-deponejon.
- Ĉi tiu dosierujo enhavas plurajn komponentojn:
  - **HEAD**: Referenco al la lasta kontribuo en la nuntempe kontrolita branĉo.
  - **konfigura dosiero**: Repository-specifaj agordoj.
  - **objekta dosierujo**: Stokas ĉiun enhavon por via datumbazo.
  - **refs dosierujo**: Tenas montrilojn al kontribuoj (esencaj branĉoj kaj etikedoj).
- Grave estas ne manuale ŝanĝi aŭ forigi dosierojn en la dosierujo `.git`, ĉar tio povus difekti vian deponejon.

### Stadado kaj Kontribuo de Viaj Unuaj Dosieroj

1. **Kreu novan dosieron en via projektdosierujo**. Ekzemple, teksta dosiero nomita `README.md`.
2. **Stadu la dosieron**. Stadado estas kiel preparado de preno de viaj ŝanĝoj antaŭ ilia kontribuo. Rulu `git add README.md` por stadi vian novan dosieron.
3. **Kontribuu la dosieron al la deponejo**. Nun, vi volas registri la prenon de viaj stadtaj ŝanĝoj. Rulu `git commit -m "Via kontribuaj mesaĝo"`. La mesaĝo devus esti mallonga priskribo de la ŝanĝoj kiujn vi faris. Por via unua kontribuo, io kiel "Inicia kontribuo" estas kutima.

### Aldonaj Notoj

- **Kontroli la statuson**: Vi povas ruli `git status` en ajna tempo por vidi la statuson de viaj dosieroj (stadita, ne stadita, sen sekvado).
- **Vidi la historion de kontribuoj**: Uzu `git log` por vidi la historion de kontribuoj.
- **Stadi ĉiujn dosierojn**: Se vi havas plurajn dosierojn kaj volas stadi ilin ĉiujn samtempe, uzas `git add .`.

Krei kaj administri Git-deponejon estas bazika kapablo en programada evoluo. Dum vi fariĝos pli konata kun Git, vi lernos pli altajn trajtojn kiel branĉado, kunfandado, kaj kunlaborado kun aliaj. Sed nun, mastrumi ĉi tiujn bazaĵojn estas signifa unua paŝo.

## Branĉiĝo en Git

Branĉiĝo estas unu el la plej potencaj trajtoj de Git, ebligante plurajn evoluoliniojn procedi sendepende. Kompreni kiel efike uzi branĉojn estas ŝlosilo al la mastrado de Git.

### Kio estas Branĉoj kaj Kial Uzi Ilin?

**Branĉo** en Git estas esence moviĝema malpeza montrilo al unu el tiuj kontribuoj. La defaŭlta branĉo kiun Git kreas por vi kiam nova deponejo estas inicialigita estas la `master` branĉo (lastatempe multaj komencis uzi `main` kiel defaŭltan nomon).

La ĉefaj kialoj por uzi branĉojn estas:

1. **Paralela Evoluo**: Branĉoj ebligas la paralelan evoluon de pluraj trajtoj aŭ riparoj. Tio estas aparte utila en teamaj medioj kie programistoj laboras samtempe pri diversaj trajtoj.

2. **Eksperimentado**: Ili provizas sablobarilon kie vi povas provi novajn ideojn sen afekti la ĉefan kodbazon, konata kiel la `master` aŭ `main` branĉo.

3. **Organizita Laborfluo**: Branĉoj helpas en la organizado de laboro pri diversaj taskoj, kiel ekzemple disvolvado de trajtoj, riparado de eraroj, kaj eksperimentado, certigante ke la ĉefa kodbazo restas stabila.

### Kreado, Ŝanĝo kaj Kunfando de Branĉoj

#### Kreado de Branĉo

1. **Komando**: `git branch <nomo-de-branĉo>`
2. **Ekzemplo**: `git branch trajto-x`
   
Tiu komando kreas novan branĉon nomatan `trajto-x`. Tamen, ĝi ne aŭtomate ŝaltas vin al la nova branĉo.

#### Ŝanĝo de Branĉoj

1. **Komando**: `git checkout <nomo-de-branĉo>`
2. **Ekzemplo**: `git checkout trajto-x`

Tio ŝaltas vian laborodirekton al la branĉo `trajto-x`.

#### Kunfando de Branĉoj

Post kiam vi faris ŝanĝojn en branĉo kaj estas preta aldoni ilin al via ĉefa branĉo (ekz., `master`), vi devos kunfandi tiujn ŝanĝojn.

1. **Ŝaltu al la branĉo kiun vi volas kunfandi en**: `git checkout master`
2. **Kunfandu la trajtan branĉon**: `git merge trajto-x`

Tio kunfandos ŝanĝojn de `trajto-x` en `master`.

### Traktado de Kunfanda Konflikto

Kunfandaj konfliktoj okazas kiam Git ne kapablas aŭtomate solvi diferencojn en kodo inter du kontribuoj. Tio kutime okazas en kunlaboraj medioj kie du programistoj faris ŝanĝojn en la sama linio de dosiero aŭ kiam unu programisto forigis dosieron dum alia modifis ĝin.

Por trakti kunfandajn konfliktojn:

1. **Identigu la konflikton**: Git listigos dosierojn kun konfliktoj post malsukcesa kunfandprovado.
2. **Redaktu la dosierojn**: Malfermu la konfliktemajn dosierojn kaj serĉu la liniojn markitajn per konflikto-markiloj (`<<<<<<<`, `=======`, `>>>>>>>`). Solvu la konfliktojn redaktante la liniojn al tio kion vi volas ke ili estu.
3. **Marku kiel solvita**: Post kiam vi riparis la konfliktojn, uzas `git add <nomo-de-dosiero>` por marki ilin kiel solvitaj.
4. **Kompletigu la kunfandon**: Rulu `git commit` por fini la kunfandon. Git aŭtomate kreos novan kontribuon kiu enkorpigos tiujn ŝanĝojn.

#### Plej Bonaj Praktikoj

- Regule tiru ŝanĝojn de la ĉefa branĉo en vian trajtan branĉon por minimumi konfliktojn.
- Solvu konfliktojn frue anstataŭ poste.
- Komuniki kun via teamo kiam laborante en la samaj dosieroj por eviti kunfandajn konfliktojn.

Kompreni kaj efike uzi branĉojn signife plibonigos vian laborfluecon en Git, ebligante pli efikan kaj organizitan evoluon.

## Git Checkout, Reset, kaj Revert

En Git, `checkout`, `reset`, kaj `revert` estas potencaj komandoj kiuj proponas malsamajn manierojn por nuligi ŝanĝojn kaj navigi tra kontribuoj. Kompreni la nuancojn de ĉiu estas gravega por efike administri vian Git-deponejon.

### Navigado Tra Kontribuoj

#### Git Checkout
- **Celado**: Ĉefe uzata por ŝalti inter branĉoj aŭ etikedoj. Tamen, ĝi ankaŭ povas esti uzata por kontroligi specifajn kontribuojn, tiel igante vian laborodirekton kongrui kun la stato de la deponejo ĉe tiu kontribuo.
- **Komando**: `git checkout [kontribuo-haŝo]`
- **Uzokazo**: Se vi volas ekzameni la staton de via deponejo en specifa punkto de ĝia historio, vi povas uzi `git checkout` kun la kontribuo-haŝo. Notu, ke tio metas vian deponejon en 'forlasita ĉefo' (detached HEAD) stato, kie ajn novaj kontribuoj kiujn vi faras estos apartaj de la resto de la historio de via projekto ĝis vi kunfandos aŭ forigos ilin.

### Nuligo de Ŝanĝoj per Reset, Checkout, kaj Revert

#### Git Reset
- **Celado**: Uzata por nuligi ŝanĝojn per reseti la aktuan branĉkapo al specifita stato. Ĝi povas esti uzata por malsegmenti ŝanĝojn, ŝanĝi la historion de kontribuoj, kaj pli.
- **Tipoj**:
  - **Mola**: `git reset --soft [kontribuo-haŝo]` konservas viajn ŝanĝojn sed resetas la ĉefon al antaŭa kontribuo. Ŝanĝoj restas en la stagitareo.
  - **Meza** (defaŭlta): `git reset [kontribuo-haŝo]` aŭ `git reset --mixed [kontribuo-haŝo]` malstadiĝas viajn ŝanĝojn kaj resetas la ĉefon al antaŭa kontribuo. Ŝanĝoj estas konservitaj sed ne en la stagitareo.
  - **Dura**: `git reset --hard [kontribuo-haŝo]` forigas ĉiujn ŝanĝojn kaj resetas la deponejon al antaŭa stato. Tio estas neantaŭenirebla kaj devas esti uzata singarde.
- **Uzokazo**: Se vi volas malsegmenti kontribuojn kaj opcie konservi aŭ forigi viajn ŝanĝojn, `git reset` estas la taŭga ilo.

#### Git Checkout
- **Celado**: Krom ŝalti branĉojn, `checkout` povas esti uzata por forigi ŝanĝojn en via laborodirekto.
- **Komando**: `git checkout -- [nomo-de-dosiero]`
- **Uzokazo**: Kiam vi faris ŝanĝojn al dosiero kaj volas reveturi ĝin al la stato ĝi havis en la lasta kontribuo, uzu `git checkout`. Tiu komando nur efikas sur la laborodirekto kaj ne ŝanĝas vian kontribuohistorion.

#### Git Revert
- **Celado**: Uzata por krei novan kontribuon kiu nuligas la ŝanĝojn faritajn en antaŭa kontribuo.
- **Komando**: `git revert [kontribuo-haŝo]`
- **Uzokazo**: Kiam vi bezonas nuligi ŝanĝojn de specifa kontribuo sed volas konservi la sekvant-historion de la projekto, `git revert` estas idealaj. Tio estas sekura maniero nuligi ŝanĝojn ĉar ĝi ne ŝanĝas la historion de la projekto.

### Komprenado de la Diferencoj Inter Ĉi Tiaj Komandoj

- **Checkout**: Ŝanĝas la staton de la laborodirekto kaj/aŭ ŝaltas branĉojn, sen ŝanĝi la projekthistorion.
- **Reset**: Movas la ĉefan kapojn de la nuna branĉo al alia kontribuo, opcie ŝanĝante la stagitareon kaj laborodirekton. Ĝi povas reskribi la projekthistorion.
- **Revert**: Kreas novan kontribuon kiu nuligas ŝanĝojn de antaŭa kontribuo, sen modifi la ekzistantan projekthistorion.

Ĉiu el ĉi tiuj komandoj havas specifan celon, kaj kompreni kiam uzi kiun komandon estas ŝlosila kapablo en Git. Memoru, komandoj kiel `git reset --hard` kaj `git checkout -- [nomo-de-dosiero]` povas konduki al perdo de laboro se uzataj senkonsidere, do ĉiam estas bone certiĝi ke vi havas sekurkopion aŭ certiĝi pri la operacio kiun vi faras.

## Laborado kun Forigitaj Deponejoj en Git

Laborado kun forigitaj deponejoj estas fundamento de Git, ebligante kunlaboron kaj kunhavigon de kodo. Kompreni kiel administri kaj interagi kun forigitaj deponejoj estas ŝlosilo por ĉiu uzanto de Git.

### Komprenado de Forigitaj Deponejoj

#### Kio estas Forigita Deponejo?
- Forigita deponejo en Git estas versio de via projekto, kiu estas gastigita sur la interreto aŭ reto ie, ofte sur servoj kiel GitHub, GitLab, aŭ Bitbucket.
- Forigajn deponejojn oni uzas por kunhavigi ŝanĝojn faritajn en kodbazo, kunlabori kun aliaj, kaj kiel rezervon de via loka deponejo.

#### Loka kontraŭ Forigita Deponejo
- La **loka deponejo** estas sur via komputilo, kie vi faras ŝanĝojn rekte.
- La **forigita deponejo** estas aparta versio kiu loĝas sur fora servilo. Vi povas push ŝanĝojn al ĝi aŭ elŝuti ŝanĝojn el ĝi.

### Aldono kaj Administraj Forigitaj Deponejoj

#### Aldono de Forigita Deponejo
1. **Komando**: `git remote add <nomo-de-forigito> <URL-de-forigito>`
2. **Ekzemplo**: `git remote add origin https://github.com/uzantonomo/deponejo.git`

Tiu komando kreas novan forigitan nomitan `origin` (konvencia nomo reprezentanta la ĉefan forigitan) montranta al la URL de la forigita deponejo.

#### Vido de Forigitaj
- Por vidi la forigitajn deponejojn asociitajn kun via loka deponejo, uzu `git remote -v`. Tio montras la nomojn de la forigitaj kaj iliajn asociajn URL-ajn.

#### Ŝanĝo de URL de Forigito
- Uzu `git remote set-url <nomo-de-forigito> <nova-URL>` por ŝanĝi la URL-on.

#### Forigo de Forigita Deponejo
- Forigu forigitan uzante `git remote remove <nomo-de-forigito>`.

### Puŝado kaj Elŝutado el Forigitaj

#### Puŝado al Forigita
- **Puŝado** rilatas al sendado de viaj lokaj ŝanĝoj al forigita deponejo.
- **Komando**: `git push <nomo-de-forigito> <nomo-de-branĉo>`
- **Ekzemplo**: `git push origin master`
- Tio puŝas viajn konfirmaĵojn de la loka branĉo `master` al la branĉo `master` de la forigita nomita `origin`.

#### Elŝutado el Forigita
- **Elŝutado** rilatas al prenadado de ŝanĝoj el forigita deponejo kaj enkorporado de ili en vian lokan deponejon.
- **Komando**: `git pull <nomo-de-forigito> <nomo-de-branĉo>`
- **Ekzemplo**: `git pull origin master`
- Tio prenas ŝanĝojn el la branĉo `master` de la forigita `origin` kaj enkorpigas ilin en vian lokan branĉon `master`.

#### Plej Bonaj Praktikoj
- Regule puŝu viajn ŝanĝojn por teni ĝisdata la forigitan deponejon.
- Regule elŝutu el la forigita por teni vian lokan deponejon ĝisdata kun la lastaj ŝanĝoj de via teamo.

### Komprenado de Preni kontraŭ Elŝuti
- `git fetch` elŝutas ŝanĝojn el forigita deponejo sed ne enkorpigas ilin en vian lokan deponejon. Tio estas utila por revizi ŝanĝojn antaŭ ilin enkorporado.
- `git pull` esence estas `git fetch` sekviĝita de `git merge`.

Laborado kun forigitaj deponejoj estas centra funkcio de Git, ebligante kunlaboron kaj efikan projekta administron. Estas necese kompreni tiujn konceptojn kaj komandojn por efika versikontrolo en teama medio.

## Git Prendi, Preni, kaj Puŝi

En Git, `fetch`, `pull`, kaj `push` estas fundamentaj komandoj uzataj por interagi kun forigitaj deponejoj. Kompreni iliajn diferencojn kaj kiam uzi ĉiun komandon estas kritika por efika kunlaboro kaj prizorgado de sinkronigita kodbazo.

### Diferencoj Inter Prendi, Preni, kaj Puŝi

#### Git Fetch
- **Celo**: `git fetch` prenas la plej novajn datumojn de la forigita deponejo (kiel branĉoj kaj iliaj respektivaj konfirmaĵoj) sed ne kunfandas ĉi tiujn ŝanĝojn en viaj lokaj branĉoj.
- **Uzo**: Ĝi estas uzata por ĝisdatigi vian lokan deponejon kun la stato de la forigita deponejo, permesante vidi pri kio aliaj laboris, sen kunfandi tiujn ŝanĝojn en viajn proprajn branĉojn.
- **Komando**: `git fetch <forigita>`

#### Git Pull
- **Celo**: `git pull` esence estas kombinaĵo de `git pull` sekviĝita de `git kunfandi`. Ĝi prenas ŝanĝojn el forigita deponejo kaj tuj kunfandas ilin en la lokan branĉon por ĝisdatigi tiun branĉon laŭ la versio de la forigita.
- **Uzo**: Ĝi estas uzata kiam vi volas kaj ĝisdatigi vian lokan deponejon por kongrui kun la forigita kaj tuj integri tiujn ŝanĝojn en vian nunan branĉon.
- **Komando**: `git pull <forigita> <branĉo>`

#### Git Push
- **Celo**: `git push` estas uzata por alŝuti la enhavon de via loka deponejo al fora deponejo.
- **Uzo**: Post konfirmado de viaj ŝanĝoj lokale, vi uzas `git push` por kunhavigi viajn ŝanĝojn kun la forigita teamaj membroj.
- **Komando**: `git push <forigita> <branĉo>`

### Sinkronigado kun Forigitaj Deponejoj

- **Prendu por Resti Ĝisdata**: Regule uzas `git fetch` por resti informita pri novaj ŝanĝoj en la forigita deponejo sen tuj integri ilin en vian lokan branĉon.
- **Prenu por Integri Ŝanĝojn**: Uzu `git pull` kiam vi estas preta kunfandi forigitajn ŝanĝojn en vian lokan branĉon. Tio ofte farigas antaŭ ol vi komencas novan trajton aŭ riparadon, por certigi ke vi laboras kun la plej freŝa versio de la kodbazo.

- **Puŝu por Dividi Viajn Laborojn**: Regule puŝas viajn ŝanĝojn por certigi ke via forigita deponejo restas ĝisdata kun via loka laboro.
- **Prenu antaŭ Puŝado**: Ĉiam prenu antaŭ ol puŝi por minimumigi konfliktojn. Tio certigas ke vi integris ajnajn freŝajn ŝanĝojn el la forigita en vian branĉon.
- **Uzu Temajn Branĉojn**: Puŝas trajto- aŭ temajn branĉojn anstataŭe ol direkti puŝi en la ĉefan branĉon. Tio gardas la ĉefan branĉon stabila kaj ebligas proceson de revizio de kodo.

### Plej Bonaj Praktikoj por Puŝado kaj Prenado

#### Prenado
1. **Prenu Ofte**: Regule preni helpas vin resti sinkrona kun la progreso de la teamo kaj reduktas la ŝancojn de gravaj kunfandkonfliktoj.
2. **Kontrolu Vian Branĉon**: Certiĝu ke vi estas sur la ĝusta branĉo antaŭ ol preni, por ke vi ne neintence kunfandu ŝanĝojn en la malĝusta branĉo.
3. **Traktu Konfliktojn Tuj**: Se preni kaŭzas konfliktojn, solvu ilin tuj. Lasi konfliktojn nesolvitaj povas kompliki la kodbazon kaj malfaciligas pluan kunfandon.

Uzi ĉi tiujn komandojn ĝuste kaj sekvi plej bonajn praktikojn helpas prizorgi puran kaj sinkronigitan laboran fluon, certigante ke ĉiuj teamaj membroj laboras kun la plej freŝa kaj senkonflikta kodo ebla.

## Avancita Branĉado kaj Kunfando en Git

Kiel viaj projektoj iĝas pli kompleksaj, avancitaj branĉadaj kaj kunfadaj teknikoj iĝas esenciaj. Ĉi tiuj praktikoj helpas prizorgi puran, organizitan, kaj efikan laborfluo, speciale en kunlaboraj medioj.

### Strategioj pri Branĉado

#### Git Flow
- **Superrigardo**: Git Flow estas branĉa modelo kiu ordonas specifajn rolojn por branĉoj kaj difinitan eldonan proceson.
- **Branĉoj**:
  - **Trajtan branĉon**: Kreitaj el `evoluigi` por novaj trajtoj.
  - **Evolua branĉo**: Branĉo kie ĉiuj trajtoj estas kunfandaj kaj testataj kune.
  - **Eldonaj branĉoj**: Branĉoj elde la `evoluigi` por finaj korektoj antaŭ iri al produktado.
  - **Ĉefo branĉo**: Tenas produkt-ready kodon.
  - **Fiksbranĉoj**: Kreitaj el `ĉefo` por rapidaj riparoj en produktado.
- **Fluo**: Trajtoj estas evoluataj en iliaj branĉoj kaj kunfanditaj returne en `evoluigi`. Kiam pretaj por eldono, eldona branĉo estas kreita el `evoluigi`, kaj post finaj korektoj, ĝi estas kunfandita en ambaŭ `evoluigi` kaj `ĉefo`. Fiksbranĉoj estas kunfanditaj returne en ambaŭ `ĉefo` kaj `evoluigi`.
- **Avantaĝoj**: Ĉi tiu modelo estas strukturita, antaŭdevidata, kaj ideala por prizorgado de pli grandaj projektoj.

### Rebazado kontraŭ Kunfado

#### Rebazado
- **Kio estas Rebazado?**: Rebazado estas la procezo de movado aŭ kunigo de serio de konfirmaĵoj al nova bazkonfirmo.
- **Uzo**: Ĝi estas uzata por integri ŝanĝojn el unu branĉo en alian, kiel `kunfado`, sed ĝi reskribas la historion de konfirmaĵoj, kreante novajn konfirmaĵojn por ĉiu konfirmo en la originala branĉo.
- **Avantaĝoj**: Rebazado rezultigas pli pura, pli linia projekthistorio.
- **Malavantaĝoj**: Ĝi povas kompliki la historion se uzata en publika branĉoj.

#### Kunfado
- **Kio estas Kunfado?**: Kunfado prenas la enhavon de fonta branĉo kaj integras ilin kun celbranĉo. En kunfada operacio, Git kreas novan konfirmon en la celbranĉo kiu ligo la historiojn de ambaŭ branĉoj.
- **Uzo**: Regule uzata por integri ŝanĝojn el unu branĉo en alian.
- **Avantaĝoj**: Ĝi konservas la kompleta historio kaj kronologia ordo.
- **Malavantaĝoj**: Povas konduki al pli komplika projekthistorio (kunfadkonfirmoj).

#### Kiam Uzi
- **Rebazado** por malgrandaj, lokaj ŝanĝoj kiuj ne estis partigitaj kun aliaj, por purigi vian branĉhistorion.
- **Kunfado** por integrado de ŝanĝoj kiuj estis partigitaj/publikigitaj aŭ por gravaj ŝanĝoj kie la konservo de la historio estas grava.

### Solvado de Komplikaj Kunfadkonfliktoj

Komplikaj kunfadkonfliktoj okazas kiam pluraj ŝanĝoj ŝanĝas la saman parton de dosiero en malsamaj manieroj. Ili postulas atentan solvon por prizorgi la integrecon de la kodbazo.

1. **Identigu Konfliktojn**: Uzu `git status` por identigi kiuj dosieroj havas konfliktojn.
2. **Redaktu Konfliktojn**: Malfermu la konfliktaĵdosierojn kaj serĉu la konfliktaĵmarkilojn (`<<<<<<<`, `=======`, `>>>>>>>`). Revizii la ŝanĝojn kaj decidi kio devus esti la fina versio.
3. **Uzu Kunfadajn Ilojn**: Por komplikaj konfliktoj, konsideru uzi grafikajn kunfadilojn kiel Meld, Beyond Compare, aŭ la kunfadilojn integratajn en IDE kiel Visual Studio Code aŭ IntelliJ IDEA.
4. **Testu Post Solvo**: Ĉiam testu vian kodo post solvi konfliktojn por certigi ke la kunfado ne rompis ion.
5. **Konfirmu la Kunfadon**: Post solvo de konfliktoj kaj testo de la kodo, aldonu la dosierojn (`git add <file>`) kaj konfirmu la kunfadon (`git commit`).

Traktado de komplikaj kunfadkonfliktoj povas ŝajni timiga komence, sed kun praktiko, ĝi fariĝas integra parto de prizorgado de kunlabora kodbazo en Git. Kompreni kiam kaj kiel uzi malsamajn branĉadstrategiojn kaj kunfadteknikojn povas signife simpligi vian disvolvadprocezon kaj plifaciligi teaman kunlaboron.
