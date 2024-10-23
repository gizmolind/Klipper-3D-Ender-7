Klipper Installation på Ender 7 med KIAUH

  Raspberry Pi (eller anden kompatibel enhed) med et fungerende operativsystem (f.eks. Raspberry Pi OS)
    Internetforbindelse
    SSH adgang til Raspberry Pi
    Ender 7 3D-printer


    

Trin 1: Forberedelse af Raspberry Pi

  Sørg for, at din Raspberry Pi er opdateret:


    sudo apt update && sudo apt upgrade -y

Installer de nødvendige afhængigheder:


    sudo apt install git python3 python3-pip -y

Trin 2: Download og Installer KIAUH

  Klon KIAUH repository:

    git clone https://github.com/th33xitus/kiauh.git ~/kiauh

Start KIAUH installationsmenuen:


    ~/kiauh/kiauh.sh

Trin 3: Installer Klipper, Moonraker og Web-UI

  Vælg Install i KIAUH-menuen og installer følgende:
        Klipper
        Moonraker
        Mainsail eller Fluidd (efter eget valg)

   Følg instruktionerne for at fuldføre installationen.

Trin 4: Hent og Anvend Konfigurationsfiler

  Klon dette repository til din Raspberry Pi:

    

    git clone https://github.com/gizmolind/Klipper-3D-Ender-7.git ~/klipper_config

Kopier de tilpassede konfigurationsfiler til din Klipper konfigurationsmappe:


    cp ~/klipper_config/*.cfg ~/klipper_config/

  Sørg for, at dine konfigurationsfiler er placeret korrekt:
        printer.cfg: Hovedkonfigurationsfilen til Klipper
        macros.cfg: Makroer for avanceret printerkontrol
        moonraker.conf: Konfiguration for Moonraker-tjenesten

Trin 5: Flash Klipper Firmware til Ender 7

   Kompilér Klipper firmware via KIAUH:
        I KIAUH-menuen, vælg Klipper og derefter Build Firmware.
        Følg instruktionerne, og vælg det rigtige kort (f.eks. STM32).
        Overfør den kompilerede klipper.bin fil til din printer (via SD-kort).

   Genstart printeren, og Klipper skulle nu køre på din Ender 7.

Trin 6: Genstart Systemet og Bekræft Opsætningen

  Genstart Raspberry Pi:

    

    sudo reboot

   Når systemet er oppe igen, åbn webgrænsefladen til Mainsail eller Fluidd via din browsers IP-adresse.

   Bekræft, at printeren er forbundet, og test nogle simple kommandoer for at sikre, at alt fungerer korrekt.

Fejlfinding

   Hvis noget ikke fungerer som forventet, kan du tjekke logfilerne i ~/klipper_logs/ for fejl.
   Du kan også køre følgende kommando for at genstarte Moonraker og Klipper:

    

sudo systemctl restart moonraker klipper
