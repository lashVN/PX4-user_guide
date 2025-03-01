# Датчики

Системи на основі PX4 використовують датчики для визначення стану рухомого засобу (це необхідно для стабілізації або увімкнення автономного керування). Стан засобу включає: позицію/висоту, курс, швидкість, швидкість польоту, орієнтацію (відносно чогось), швидкість обертання в різних напрямках, рівень заряду батареї тощо.

PX4 *мінімально потребує* гіроскоп, акселерометр, магнетометр (компас) та барометр. Всі автоматичні режими, а також деякі ручні/допоміжні режими потребують GPS або іншу систему позиціювання. Апарати з фіксованим крилом та VTOL повинні додатково включати датчик швидкості польоту (дуже рекомендується).

Мінімальний набір датчиків вбудований в політні контролери [Pixhawk Series](../flight_controller/pixhawk_series.md) (а також він може бути в контролерах інших платформ). До контролера можна приєднати додаткові/зовнішні датчики.

Нижче ми описуємо деякі зовнішні датчики.
<a id="gps_compass"></a>

## GPS & Компас

PX4 підтримує чисельні приймачі Системи Глобальної Супутникової Навігації (GNSS) та компаси (магнітометри). Він також підтримує кінематичні GPS приймачі реального часу (RTK), які розширяють GPS системи до точності сантиметрового рівня.

Рекомендуємо використовувати зовнішній "комбінований" модуль GPS/компаса, встановлений якомога далі від ліній живлення мотора/ESC - як правило на підставці або крилі (для апарату з фіксованим крилом).

![GPS + Компас](../../assets/hardware/gps/gps_compass.jpg)

Опції апаратного забезпечення GPS/компаса викладені в:
- [GPS/компас](../gps_compass/index.md)
- [RTK GNSS (GPS)](../gps_compass/rtk_gps.md)

::: info [Pixhawk-series](../flight_controller/pixhawk_series.md) controllers include an *internal* compass. Через електромагнітні перешкоди, спричинені кабелями живлення, близькими до політного контролера, наполегливо рекомендується не покладатися на внутрішній компас для оцінки курсу та замість нього використовувати зовнішній. :::

## Швидкість польоту

Датчики швидкості польоту *дуже рекомендуються* для планерів VTOL та апаратів літакового типу.

Це важливо, бо автопілот не має інших засобів для виявлення звалювання. Т. як швидкість польоту літака відносно повітря гарантує підіймальну силу, а не швидкість відносно землі!

![Цифровий датчик швидкості польоту](../../assets/hardware/sensors/airspeed/digital_airspeed_sensor.jpg)

Для додаткової інформації та рекомендованого апаратного забезпечення дивіться: [Датчики швидкості польоту](../sensor/airspeed.md).

## Відстань

Датчики відстані використовуються для плавної посадки, уникнення інших об'єктів та слідування місцевості.

PX4 підтримує багато доступних датчиків відстані, які використовують різні технології та підтримують різні діапазони та функції. Для отримання додаткової інформації дивіться: [Датчики відстані](../sensor/rangefinders.md).

<img src="../../assets/hardware/sensors/lidar_lite/lidar_lite_1.png" title="lidar_lite_1" width="500px" />

## Оптичний потік

[Датчики оптичного потоку](../sensor/optical_flow.md) використовують камеру та датчик відстані направлені вниз для оцінки швидкості. PX4 комбінує дані з датчика з інформацією з інших джерел позиціювання (наприклад, GPS), щоб забезпечити більш точну фіксацію позиції. Цей датчик можна використовувати у приміщенні, якщо немає сигналу GPS.

![Зображення датчику оптичного потоку ARK Flow](../../assets/hardware/sensors/optical_flow/ark_flow.jpg)


## Дивіться також

- [Периферійне апаратне забезпечення](../peripherals/README.md) містить документацію для інших датчиків, наприклад [Монітори батарей/живлення](../power_module/README.md)), [Системи нотифікації щодо трафіку в повітрі](../peripherals/adsb_flarm.md), [Тахометри](../sensor/tachometers.md).
- [Базова збірка](../assembly/README.md) містить посібники швидкого старту з політними контролерами. Вони пояснюють, як під'єднати основні датчики до конкретного політного контролера.
- Розділи в [Політний контролер](../flight_controller/README.md) часто містять інформацію про їх підключення.
