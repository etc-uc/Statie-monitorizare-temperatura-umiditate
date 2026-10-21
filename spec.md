#Specificații:

##Denumire:
Stație de monitorizare a temperaturii și umidității.

##Scop:
Realizarea unui sistem embeeded pentru masurarea temperaturii si umidității ambientale și afișarea valorilor pe un ecran LCD.

##Componente hardware:
- STM32F103C8T6 – microcontroler ARM Cortex-M3 pe 32 de biți;
- DHT22 / AM2302 – senzor de temperatură și umiditate;
- LCD 16×2 cu adaptor I2C – afișarea valorilor măsurate;
- regulator de tensiune de 3,3 V și condensatoare de decuplare;
- conector SWD – programarea și depanarea microcontrolerului;
- rezistențe și alte componente pasive necesare;
- PCB proiectat în KiCad, pe care va fi montat microcontrolerul.

##Funcționalități:
- măsurarea temperaturii ambientale;
- măsurarea umidității relative;
- afișarea temperaturii în grade Celsius;
- afișarea umidității în procente;
- actualizarea periodică a valorilor pe LCD;
- tratarea erorilor de citire a senzorului.

##Periferice utilizate:
- GPIO – gestionarea semnalelor digitale;
- I2C – comunicația cu afișajul LCD;
- Timer – realizarea temporizărilor și actualizarea periodică a datelor;

##Software si instrumente:
- limbaj de programare C;
- STM32CubeIDE – dezvoltarea și compilarea programului;
- KiCad – proiectarea schemei electrice și a PCB-ului;
- ST-LINK – programarea și depanarea microcontrolerului;

##Criterii de testare:
- citirea corectă a temperaturii și umidității;
- afișarea valorilor pe LCD;
- actualizarea periodică a datelor;
- verificarea comunicației dintre microcontroler și periferice;
- verificarea funcționării și alimentării corecte a circuitului.

##Rezultat final:
Obținerea unei stații de monitorizare a temperaturii si umidității realizată pe un PCB propriu si controlata de microcontrolerul STM32F103C8T6.
