##Alegerea microcontrolerului:
Pentru realizarea stației de monitorizare a temperaturii și umidității am analizat trei microcontrolere bazate pe arhitectura ARM:
-STM32F103C8T6;
-STM32F401CCU6;
-NXP LPC1768;

Comparația ia în considerare frecvența de funcționare, performanța procesorului, suportul pentru calcule în virgulă mobilă, instrucțiunile DSP, perifericele disponibile și costul estimativ.

##Tabel comparativ:

| Caracteristică | STM32F103C8T6 | STM32F401CCU6 | NXP LPC1768 |
|---|---|---|---|
| Producător | STMicroelectronics | STMicroelectronics | NXP |
| Arhitectură CPU | ARM Cortex-M3 | ARM Cortex-M4 | ARM Cortex-M3 |
| Dimensiune | 32 biți | 32 biți | 32 biți |
| Frecvență maximă | 72 MHz | 84 MHz | 100 MHz |
| Memorie Flash | 64 KB | 256 KB | 512 KB |
| Memorie SRAM | 20 KB | Până la 64 KB | 64 KB |
| FPU | Nu | Da | Nu |
| ADC | 12 biți | 12 biți | 12 biți |
| Interfețe | I2C, SPI, USART, USB, CAN | I2C, SPI, USART, USB, SDIO | I2C, SPI, UART, USB, CAN, Ethernet MAC |
| Capsulă | LQFP-48 | UFQFPN-48 | LQFP-100 |
| Cost orientativ | Aproximativ 34 lei | Aproximativ 22–25 lei | Aproximativ 74 lei |
| Potrivire pentru proiect | Foarte bună | Foarte bună | Bună, dar poate fi supradimensionat |

##Justificarea alegerii:
STM32F103C8T6 a fost ales deoarece oferă suficiente resurse pentru citirea senzorului DHT22 și afișarea valorilor pe un LCD 16x2 cu interfață I2C. Funcționează la 72 MHz, are o arhitectură ARM Cortex-M3 
pe 32 de biți și dispune de interfețele necesare proiectului.
Capsula LQFP-48 permite realizarea unui PCB personalizat în KiCad, iar disponibilitatea documentației tehnice facilitează programarea și depanarea circuitului.

##Senzorul DHT22 (AM2302)
Am ales senzorul DHT22 deoarece poate măsura atât temperatura, cât și umiditatea relativă a aerului, fiind potrivit pentru scopul proiectului. Acesta transmite datele digitale către microcontroler printr-o 
singură linie de comunicație, reducând numărul de conexiuni necesare. În plus, oferă o precizie potrivită pentru o stație de monitorizare destinată utilizării demonstrative.

##Afișajul LCD 16x2 cu interfață I2C
Am ales un afișaj LCD cu 16 coloane și 2 rânduri pentru a putea prezenta simultan valorile temperaturii și umidității. Interfața I2C reduce numărul de pini necesari pentru comunicarea cu microcontrolerul, folosind 
liniile SDA și SCL. Astfel, conexiunile sunt simplificate, iar mai mulți pini rămân disponibili pentru alte funcții. Afișajul LCD este deja disponibil, ceea ce reduce costul total al proiectului.

##Regulatorul de tensiune de 3,3V
Am ales un regulator de tensiune de 3,3 V pentru a asigura alimentarea corespunzătoare a microcontrolerului STM32F103C8T6 și a componentelor care funcționează la această tensiune. Regulatorul contribuie la obținerea 
unei tensiuni stabile în circuit. Modelul concret va fi ales în funcție de tensiunea de intrare, curentul necesar și componentele conectate.

##Condensatoarele de decuplare
Am ales condensatoare de decuplare pentru a reduce perturbațiile și variațiile rapide ale tensiunii de alimentare. Acestea se montează în apropierea pinilor de alimentare ai microcontrolerului și contribuie la funcționarea 
stabilă a circuitului.

##Circuitul de reset și pinul BOOT0
Am inclus conexiunile necesare pentru resetarea microcontrolerului și configurarea pinului BOOT0. Butonul de reset permite repornirea manuală a sistemului, iar configurarea corespunzătoare a pinului BOOT0 asigură pornirea 
microcontrolerului din memoria Flash în modul normal de funcționare.

##Conectorul de programare și depanare SWD
Am ales o interfață SWD (Serial Wire Debug) pentru programarea microcontrolerului și depanarea codului C. Aceasta permite conectarea unui programator compatibil, precum ST-LINK, fără a fi necesară scoaterea microcontrolerului 
de pe placa PCB.

##Componente pasive și conectori
Rezistențele, conectorii și celelalte componente pasive sunt necesare pentru realizarea conexiunilor electrice, stabilirea nivelurilor logice și conectarea senzorului, afișajului și sursei de alimentare. Valorile și tipurile 
acestora vor fi stabilite în etapa de proiectare a schemei electrice.

##Crearea fișierului:
Acest fișier a fost realizat cu ChatGPT, cu promptul: "Trebuie să mai fac un fișier numit alegerea pieselor in care să am trei microcontrolere, printre care și al meu, și, comparativ cu celelalte, să spun de ce l-am ales pe acesta, 
în funcție de performanță, MHz, MIPS, floating point, digital single processing, periferice și cost. Trebuie să fac acelasi lucru și pentru celelalte piese, dar fără tabel.".
