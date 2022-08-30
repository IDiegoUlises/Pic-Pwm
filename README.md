# Pic 16F887 Pwm

<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/16f887-Pic.png"  />

* **Los Pines CCP1 y CCP2 funcionan como salidas de Pwm**
* Vdd: Positivo del microcontrolador
* Vss: Negativo del microcontrolador
* Clkin: Osicilador conectado a negativo
* Clkout: Osicilador conectado a negativo


### Codigo
```c
#include <16f887.h> //Nombre del microcontrolador
#fuses xt,nowdt  //para osciladores de 4 MegaHertz se usa xt para mayores usa hs
#use delay(clock=4M) //Velocidad del oscilador, la "M" signfica mega

int frecuencia = 255; //Frecuencia del PWM
int preescaler = 1; //Solo se puede configurar el valor de 1

void main()
{
   setup_timer_2(t2_div_by_16, frecuencia, preescaler); //Configuramos el timer2 ya que la señal pwm se genera con ayuda del reloj del timer2
   setup_ccp1(ccp_pwm); //Asignamos el puerto ccp1 como puerto de pwm
   
   while(true)
   {  
     for(int pwm = 0; pwm<1024; pwm++)
      {
         set_pwm1_duty(pwm); //Enviamos una señal pwm de 0 a 1024
         delay_ms(10); //Retraso en milisegundos
      }
      
      //Envia una señal pwm para apagar el led
      set_pwm1_duty(0);
   }
}
```
### Compilar en Css Compiler
<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/Codigo-En-Imagen.png"  />

### Conectar el Pic al Pickit 
<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/Pickit3.jpg" width="1000" height="500" />

### Subir el archivo Hex al Pickit 
<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/Importar-Hex.png"  />

### Luego subir el programa al microcontrolador con "Write"
<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/Write-pickit.png"  />

### Conexion
<img src="https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/Imagen-en-Fritzing.png" />

### Funcionamiento
![](https://github.com/IDiegoUlises/Pic-Pwm/blob/main/Images/GIF-Pwm.gif)
