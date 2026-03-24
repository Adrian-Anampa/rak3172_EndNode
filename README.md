## Envio de datos del sensor SCD30 a una red de servidor local mediante el protocolo LoRaWAN

                                         /***** Envio de datos a una red de servidor mediante el protocolo LoRaWAN  *****/ 
                                         *******************************************************************

                                       /// Este proyecto fue construida utilizando STM32CubeIDE con librerias HAL ///
Para utilizar el modulo RAK3172 para el envio de paquetes de datos del sensor SCD30 y la lectura del ADC del modulo
al servidor local del gateway , debe seguir los siguientes pasos:
- Entrar a la carpeta debug y descargar solo el archivo Lorabasicop2.bin de este repositorio
- Abrir el STM32CubeProgrammer y conectar el modulo FTDI al modulo RAK3172 de la siguiente manera

                         Modulo RAK3172    ||    MODULO FTI
                   ---------------------------------------
                          3.3V                VCC (3.3 V)
                          GND                 GND 
                          UART2 TX            RX
                          UART2 RX            TX
                          Boot 0              VCC (3.3 V)
                  -----------------------------------------
- En stm32cubeProgrammer configurar la conexion por UART , conectarse y luego darle a Download para bajar el programa.
- Desconecta el VCC del pin Boot 0 y realiza las conexiones del esquematico mostrado en el informe de resultados.
- Al terminar las conexiones y alimentar todo con voltaje 3.3V el rak3172 iniciara el envio de paquetes al gateway

Para modificar este proyecto a una nueva version , realice lo siguientes pasos:
- Descarga todo el contenido de este repositorio.
- Renombra la carpeta que descargaste por Lorabasicop2 , esto es para que se pueda compilar sin errores
- Por ultimo añade la nueva configuracion en el .ioc o la programacion en el archivo lora_app.c o main.c

-- Acerca del sensor SCD30 ::

               Sensor address ( 7 bits )            ::  0x61 
               Sensor address with read argument:1  ::  0xC3
               Sensor address with write argument:0 ::  0xC2
               Command that starts measurement      ::  0x0010 
               Command that gets  ready status      ::  0x0202
               Command that reads measurement       ::  0x0300

-- Conexión I2C2 ::

                       SCD30 SENSOR    ||    STM32WL
                   ---------------------------------------
                          VIN                 3.3V
                          GND                 GND 
                          SDA                 PA11
                          SCL                 PA12
                  -----------------------------------------
