#include <Wire.h>     // libreria de comunicacion por I2C
#include <LCD.h>      // libreria para funciones de LCD
#include <LiquidCrystal_I2C.h>    // libreria para LCD por I2C
LiquidCrystal_I2C lcd (0x27, 2, 1, 0, 4, 5, 6, 7); // DIR, E, RW, RS,
// D4, D5, D6, D7
float A = 3; // guardamos en la variable A el valor  
float B = 8; // guardamos en la variable B el valor
float Suma = A + B; // en la variable guardamamos la operacion suma

void setup ()
{
Serial.begin (9600); //establecemos una conexion entre pc y arduino
lcd.setBacklightPin(3,POSITIVE);  // puerto P3 de PCF8574 como positivo
lcd.setBacklight(HIGH); // habilita iluminacion posterior de LCD
lcd.begin(16, 2); // 16 columnas por 2 lineas para LCD 1602A
lcd.clear(); // limpia pantalla
}
void loop ()
{
Serial.print ("A = "); //se imprime el dato A 
Serial.println (A); // se imprime el valor A
Serial.println ("------------"); // renglon de separacion 
Serial.print ("B = "); // se imprime el dato B
Serial.println (B); // se imprime el valor B
Serial.println ("------------"); // renglon de separacion 
Serial.print ("Suma = "); // se imprime el dato suma
Serial.println (Suma); // se imprime el valor de la suma 
Serial.println ("------------"); // renglon de separacion 
lcd.setCursor(0, 0); // ubica cursor en columna y linea
lcd.print("A= "); // escribe texto
lcd.setCursor (3, 0); // ubica cursor en columna y linea
lcd.print(A); // escribe texto
lcd.setCursor(8, 0); // ubica cursor en columna y linea
lcd.print("B= "); // escribe texto
lcd.setCursor (11, 0); // ubica cursor en columna y linea
lcd.print(B); // escribe texto
lcd.setCursor (0, 1); // ubica cursor en columna y linea
lcd.print("Suma = "); // escribe texto
lcd.setCursor(7, 1); // ubica cursor en columna y linea
lcd.print(Suma); // escribe texto
delay (750); // tiempo para mostrar los valores
}

