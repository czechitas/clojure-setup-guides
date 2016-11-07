# Nastavení macOS 10.12

## Cílový stav

Po dokončení všech kroků nastavení bychom měli získat systém, na kterém bude následující software, abychom mohli psát kód v Clojure.

- [Java](https://java.com/): virtuální stroj, nad kterým Clojure běží a je tady absolutní nezbytností.
- [Leiningen](https://leiningen.org/): nástroj pro správu Clojure projektů, který je de facto nezbytností pro jakýkoli vývoj v Clojure. Zároveň instaluje samotný Clojure.
- [Gorilla REPL](http://gorilla-repl.org/index.html): prostředí pro spouštění, experimentování, rychlou zpětnou vazbu a sdílení Clojure kódu.


## Terminál a oprávnění

Při instalaci budeme používat terminál, někdy také označovaný jako příkazová řádka. Terminál je standardní součástí macOS.

![Spuštění Terminálu přes Spotlight](images/macos/launch-terminal.png)

Některé úkony vyžadují vyšší oprávnění a je na potřeba mít typ účet správce. Pokud je v systému pouze jeden uživatelský účet, tak se téměř jistě jedná o správce.

![Správcovský účet](images/macos/administrator-account.png)

Základy práce s terminálem jsou nad rámec této příručky.

## Instalace Javy

Stáhneme si [Java JDK z webu Oracle](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)

![Stažení JDK 8 pro macOS](images/macos/download-java.png)

Stránka pro stažení nabízí spoustu možností. Pro nás je nejlepší stáhnout hned první z nabízených balíků nadepsaný *Java SE Development Kit* s číslem verze. Před stažením je potřeba souhlasit s licenčními podmínkami, což se provede vybráním volby hned pod výše zmíněným nadpisem. Pak už můžeme stáhnout instalátor pro Mac OS X (historické označení pro macOS).

Po stažení Javu nainstalujeme klasickým postupem pro instalaci software staženého z internetu. Připojíme DMG soubor. Spustíme instalátor a krok po kroku dojdeme až na konec instalačního procesu. Během toho budeme dotázáni na naše heslo pro potvrzení a autorizování změn v systému. DMG soubor vysuneme a můžeme ho případně smazat, pokud jsme tak nevybrali na konci instalace.

![Spuštění instalátoru Javy](images/macos/install-java.png)

Na konec celé instalační procedury v Terminálu ověříme, že máme Javu nainstalovanou a že je aktivní:

```bash
java -version
```

Výsledkem by měl být podobný výpis s tím, že konkrétní čísla verze Javy se mohou mírně lišit.

![Ověření verze Javy](images/macos/verify-java.png)


## Instalace Leiningenu

Instalace Leiningen bude oproti Javě probíhat celá v Terminálu.

**Poznámka**: Pokud náhodou máte nainstalovaný správce balíčků [Homebrew](http://brew.sh/), Leiningen lze instalovat pouhým spuštěním `brew install leiningen`. Poté je možné přejít rovnou k instalaci Gorilla REPL.

Nejprve je potřeba vytvořit adresář, kde budeme mít spustitelné soubory. Právě takovým souborem potom budeme Leiningen, respektive naše Clojure projekt, ovládat. Nejsnazší je vytvořit v systému novou složku, k čemuž je ale potřeba oprávnění správce, proto následující příkaz opět vyžadovat heslo:

```bash
sudo mkdir -p /usr/local/bin
```

Nyní stáhneme skript `lein`, který uložíme do souboru v právě vytvořeném adresáři:

```bash
curl -fsSLO https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
sudo mv lein /usr/local/bin
```

Poté změníme práva k souboru `lein` tak, aby šel spouštět:

```bash
sudo chmod a+x /usr/local/bin/lein
```

Nakonec instalaci dokončíme spuštěním staženého skriptu:

```bash
lein
```

Leiningen doinstaluje další nutné soubory a následně zobrazí nápovědu, jak se s ním pracuje.


## Vytvoření projektu s Gorilla REPL

Prostředí Gorilla REPLu se spouští v rámci projektu, proto nejprve takový projekt musíme vytvořit.

Nejprve si ale vytvoříme nový adresář pro vývoj software obecně. V zásadě ale není problém vše provádět přímo v domovském adresáři nebo například ve složce `Dokumenty`.

```bash
mkdir ~/Developer
```

Přesunem se do adresáře, kde budeme vytvořet projekt s Gorilla REPLem. V mém případě se jedná o nově vytvořený adresář `dev`.

```bash
cd ~/Developer
```

Vytvoříme nový projekt přes Leiningen:

```bash
lein new czechitas-clj
```

Přesuneme se do nově vytvořeného projektu:

```bash
cd czechitas-clj
```

Upravíme `project.clj` tak, že do něj přidáme novou konfiguraci s Gorilla pluginem pro Leiningen.

```bash
open -e project.clj
```

Do souboru přidáme konfiguraci: `:plugins [[lein-gorilla "0.3.6"]]`.

![Přidání Gorilla REPL](images/macos/gorilla-plugin.png)

Spustíme Gorilla REPL:

```bash
lein gorilla
```

Začnou se doinstalovávat závislosti a samotný Gorilla REPL. Nakonec se ale spustí a náš REPL si můžeme otevřít v prohlížeči na zobrazené adrese.

![Spuštění Gorilla REPL](images/macos/launch-gorilla.png)