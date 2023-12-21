# Включение и выключение ПК используя esp8266 с реле.   
Поддерживается Яндекс Алиса и просто http(get) запросы   
Запросы выполняются следующим образом для цикла открытия и закрытия реле:  
> http://123.456.789.101/open

Для работы нам потребуется провода ,плата NodeMcu3 ESP8266 и модуль реле, схема подключения следующаяя:  
![image](https://github.com/kulisworm/esp8266pccontrol/assets/59212398/710b0a74-acc3-4de6-88f7-1ade025d7c8d)

---  

## Прошивка  
Скачиваем **wifirele.ino** и заходим в Arduino Ide. Далее заходим **"Файл">"Настройки"** ,находим внизу "Дополнительные ссылки для Менеджера плат" и вставляем туда эту [ссылку](http://arduino.esp8266.com/stable/package_esp8266com_index.json "Просто скопируй меня, куда просят!")  

Отлично! Теперь шьем нашу плату и переходим к следующему шагу!  

 ---  
 
## Монтаж  
Теперь залазим в комп ,швиряем туда нашу самоделку и ищем провода(Обычно желтые и белые), ведущие от кнопки включения(POWER SW), нам необходимо их аккуратно оголить и подключить выводы с реле (L1 И L) к этим проводам, то есть парралельным типом подключения
***Важный момент: не вздумайте класть голую плату на метталический корпус пк, обязательно подложите диэлектрик!***  

---  

## Теперь вопрос с питанием платы  
Тут у нас три варианта:
* Подключение к незанятым пинам USB непосредственно на самой плате
* Подключение к дежурным 5В с блока питания 20пин
* Подключение через MicroUsb тупо через порты ПК
### Питание от пинов USB:  
На каждой материнской плате есть пины для подключения USB портов, редко, когда заняты все, обычно один все таки да свободен.  
![image](https://ae01.alicdn.com/kf/HT1maOzFQpXXXagOFbX0/206256178/HT1maOzFQpXXXagOFbX0.jpg?size=89762&height=426&width=800&hash=89b17764cde4898a722ebe37beabce59)  
Именно на этих портах ,даже в выключенном состоянии ПК имеется нужное нам ,дежурное 5В. Ищем распиновку конкретно вашей материнской платы и подключаем минус к пину GND ,а плюс к пину Vin. Питание готово.  

### Питание от БП  
В интернетах есть такая картинка  
![image](https://github.com/kulisworm/esp8266pccontrol/assets/59212398/cdab7080-040f-4859-b406-592282cdf00b)  
Я бы не рекомендовал этот способ, так как он довольно небезопасный. Легко перепутать контакты и что-то задеть. Если будете его использовать ,то 5VSB с ПК подключается на Vin еспшки, а любой черный провод с ПК, на GND есп  
### MicroUSB  
Я не стал париться, подключил плату через MicroUSB прямо в порт USB ПК, выглядит не особо красиво, но не запарно ,а главное - работает  

---  

## Подключение к Яндекс Алисе  
Регаемся в [Домовенке Кузе](https://alexstar.ru/ "ахахаха домовенок кузя") и добавляем новое http(get) правило, я думаю, там разберетесь без мануала. Предварительно необходимо открыть порты на роутере для esp. 

 ---
 
# Спасибо за прочтение!
Если есть какие-то замечания или вопросы, буду рад выслушать и ответить в [Телеграмме](https://t.me/onlykhamenko "Мой телеграм!") или на почте ilya.khamenko@yandex.ru
