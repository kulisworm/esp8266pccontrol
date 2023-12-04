# Включение и выключение ПК используя esp8266 с реле.   
Поддерживается Яндекс Алиса и веб интерфейс  
Работает все тупо на http запросах, просто и сердито  
Запросы выполняются следующим образом для включения и выключения соответственно:  
> http://ipyouresp/LED=OFF  
> http://ipyouresp/LED=ON  

Из-за ошибок в коде "OFF" используется для включения и "ON" для выключения  
Для работы нам потребуется провода ,плата NodeMcu3 ESP8266 и модуль реле, схема подключения следующаяя:  
![image](https://github.com/kulisworm/esp8266pccontrol/assets/59212398/710b0a74-acc3-4de6-88f7-1ade025d7c8d)  
Теперь залазим в комп ,швиряем туда нашу самоделку и ещем провода(Обычно желтые и белые), ведущие от кнопки включения(POWER SW), нам необходимо их аккуратно оголить и подключить выводы с реле (L1 И L) к этим проводам  
Важный момент: не вздумайте класть голую плату на метталический корпус пк, обязательно подложите диэлектрик!  
# Теперь вопрос с питанием платы  
Тут у нас три варианта:
* Подключение к незанятым пинам USB непосредственно на самой плате
* Подключение к дежурным 5В с блока питания 20пин
* Подключение через MicroUsb тупо через порты ПК
### Питание от пинов USB:  
На каждой материнской плате есть пины для подключения USB портов, редко, когда заняты все, обычно один все таки да свободен. Именно на этих портах ,даже в выключенном состоянии ПК имеется нужное нам ,дежурное 5В. Ищем распиновку конкретно вашей МП и подключаем минус к пину GND ,а плюс к пину Vin. Питание готово.  

### Питания от БП
В интернетах есть такая картинка  
![image](https://github.com/kulisworm/esp8266pccontrol/assets/59212398/cdab7080-040f-4859-b406-592282cdf00b)  
Я бы не рекомендовал этот способ, так как он довольно небезопасный. Легко перепутать контакты и что-то задеть. Если будете его использовать ,то 5VSB с ПК подключается на Vin еспшки, а любой черный провод с ПК, на GND есп  

### MicroUSB

Я не стал париться, подключил плату через MicroUSB прямо в порт USB ПК, выглядит не особо красиво, но не запарно ,а главное - работает
