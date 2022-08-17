# Pic-Pwm

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
