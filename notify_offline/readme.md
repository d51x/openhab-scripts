**gDeviceStatus** - группа switch-айтемов, которые содержат статусы устройств (ON/OFF) 

**Описание:**
-  правило смотрит изменение членов группы.
-  если происходит изменение с ON на OFF, то запускается таймер и с заданой периодичностю формирует текст уведомления
-  если происходит изменение с OFF на ON, то таймер останавливается и формируется единичное уведомление
 
 Правило устаналвивает текст уведомления у айтема ***vTelegramMessage***
 
 Нужно второе правило, которое реагирует на изменение ***vTelegramMessage*** и отправляет его содержимое нужным вам методом

**Правило**:
 when member of gDeviceStatus was
 then execute script

 **ECMAScript (ECMAScript 262 Edition 11)**

 
 Скрипт использует ***item metadata***, каждому атему можно задать индивидуальные значения:
 ***remindTime*** - с указанной периодичностью будет формироваться оповещение о недоступности устройства, можно задавать в формате, например, 4m - 4 минуты, 1h - 1 час, 2d - 2 дня
 ***deviceName*** - имя уствроства, которое будет отправляться в сообщении, если не задано, то используется item.label,  если не нравится в качестве имени устройства item.label, то задайте для айтема - deviceName

 **Дополнительные items для правила:**
 
 ***defaultUnavailableDeviceReminderTime*** - задается время напоминания по-умолчанию для всей айтемс, кроме тех, у кого задано индивидуально через metadata, если нет айтема, то по дефолту используется значение 30m - 30 минут
	  
 