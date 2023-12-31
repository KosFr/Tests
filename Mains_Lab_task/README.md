# Тестовое задание в Mains Lab

## Задание

Требуется с помощью анализа данных найти потенциальное мошенничество со стороны клиники в оказанных медицинских услугах по ДМС.

Что такое мошенничество? Систематическое искажение информации в реестре оказанных медицинских услуг с целью получения прибыли. 
- ”клиника один раз выставила выставила услугу за 2000 рублей вместо услуги за 1000 рублей” - не мошенничество, т.к. нет системности;
- ”клиника назначила и провела исследование тиреотропного гормона при диагнозе простуда (данный анализ при данном диагнозе не нужен)” - не мошенничество, т.к. услуга реально была проведена и диагноз был поставлен корректно - нет искажения информации и нет системности;
- “каждому пришедшему пациенту клиника приписывает услугу тестирование на COVID вне зависимости от того, был ли реально проведен тест” - мошенничество, т.к. есть системность и искажение информации.

## Описание данных

- row_id - уникальный идентификатор строки данных
- butch_id – уникальный идентификатор счета
- service_id – уникальный идентификатор медицинской услуги
- service_name - наименование медицинской услуги
- service_quantity - количество медицинских услуг
- service_date - дата оказания медицинской услуги
- service_amount - сумма выплат (стоимость оказанных услуг в рублях)
- icd_codes – коды диагнозов МКБ-10 застрахованного по медицинской услуге
- insured_id - уникальный идентификатор застрахованного
- insured_age – возраст застрахованного
- insured_gender – пол застрахованного
- provider_id – уникальный идентификатор клиники
- service_code – код проклассифицированной медицинской услуги
- service_code_name – наименование проклассифицированной медицинской услуги

## Требования к результату

- Инструмент - python-скрипт или jupyter notebook c расчетом + файл requirements.txt.
- Результат должен содержать код для поиска мошенничества + результат обработки выборки данных с помощью скрипта + текстовое обоснование, почему отмеченные скриптом кейсы являются подозрительными
- Оцениваться будет корректность формулировки гипотезы, правильность расчетов и выводов + оформление отчета.
- Обязательное требование к результату - найти хотя бы одну потенциально мошенническую схему/паттерн в данных. Т.е. если вы проверили 10 идей и ни одна не подтвердилась (не нашлось кейсов с данными видом мошенничества) - это плохой результат.

## Полученный результат

Была проведена проверка четырех гипотез:
1. Запись исследований как индивидуальных вместо комплексных (например, в рамках проф осмотра);
2. Запись пациента на повторный первичный прием к специалисту (первичный прием стоит дороже);
3. Запись пациентов на исследования, которые им не полагаются по половому признаку;
4. Запись пациентов на "консультацию перед процедурой", после которой сама процедура не проводится.

Выяснилось, что гипотезы №2 и №4 имеют под собой фактическое основание, т.е. были найдены систематические случаи злоупотреблений.
Гипотеза №1 остается перспективной, но требует дополнительной работы по фильтрации данных и поиску нужных диагнозов из МКБ.