## tmp102_getTempC

Guida all'interrogazione del sensore attraverso la libreria sparkfun ufficiale:

[I'm an inline-style link with title](https://github.com/sparkfun/SparkFun_TMP102_Arduino_Library)

## Inclusione della libreria

    #include <Wire.h> // Used to establied serial communication on the I2C bus
    #include <SparkFunTMP102.h> // Used to send and recieve specific information from our sensor

Si dichiara un oggetto di tipo TMP102:

    TMP102 tmpSensor;

## Fase di setup

    Serial.begin(9600); Si inizializza l'interfaccia asincrona per la comunicazione con il PC
    Wire.begin(); //Si inizializza il modulo seriale sincrono I2C per la comunicazione con il sensore tmp102

     /*It will return true on success or false on failure to communicate. */

Si interroga il sensore per vedere se risponde all'indirizzo 0X48:
     
    if(!tmpSensor.begin())
    {
      Serial.println("Cannot connect to TMP102.");
      Serial.println("Is the board connected? Is the device ID correct?");
      while(1); //Si blocca l'esecuzione
      }
      
    Serial.println("Connected to TMP102!");
    delay(100);


## Fase di loop

Mettiamo in funzione il sensore in modo che inizi ad acqusire. Di default effettua 4 conversioni al secondo:

     
    tmpSensor.wakeup();

Leggiamo il registro che contiene la temperatura:

     float temperatura = tmpSensor.readTempC();

Mettiamo il sensore in modalità basso consumo:

    tmpSensor.sleep();

Stampiamo la temperatura:

    Serial.print("Temperatura: ");
    Serial.print(temperatura);

Aspettiamo 2 secondi:

    delay(2000);

  



