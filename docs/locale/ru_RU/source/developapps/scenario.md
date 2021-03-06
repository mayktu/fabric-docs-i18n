# Сценарий

**Аудитория**: Архитекторы, разработчики приложений и смарт-контрактов, профессионалы
бизнес-функций

В этом разделе мы опишем бизнес-сценарий, в котором шесть организаций используют
PaperNet, бизнес-сеть коммерческих ценных бумаг, построенную на основе Hyperledger
Fabric, для эмиссии, купли/продажи и погашения коммерческих ценных бумаг. Мы используем
этот сценарий для того, чтобы очертить требования к разработке приложений и смарт-контрактов
коммерческих ценных бумаг.

## Сеть PaperNet

Сеть PaperNet является сетью обращения коммерческих бумаг, которая позволяет должным
образом авторизованным участникам эмитировать, торговать и рейтинговать коммерческие
ценные бумаги.

![develop.systemscontext](./develop.diagram.1.png)

*Диаграмма сети PaperNet. Шесть организаций используют ее для эмиссии, купли/продажи,
погашения и присваивания рейтинга коммерческим ценным бумагам. MagnetoCorp
эмитирует и погашает коммерческие ценные бумаги. DigiBank, BigFund, BrokerHouse и
HedgeMatic торгуют коммерческими ценными бумагами друг с другом. RateM предоставляет оценку риска
(рейтинг) различных выпуском коммерческих ценных бумаг.*

Давайт посмотрим, как MagnetoCorp использует PaperNet и коммерческие ценные бумаги
в своем бизнесе.

## Представляем действующих лиц

MagnetoCorp - уважаемая компания, производитель беспилотных электромобилей.
В начале апреля 2020 г. MagnetoCorp получила крупный заказ на производство
10,000 машин "Модель D" для Daintree, нового игрока на рынке персональных средств
передвижения. Несмотря на то, что этот заказ - большая удача для MagnetoCorp, условия
заказа подразумевают, что Daintree оплатит поставку автомобилей только при начале
поставок 1 ноября, на шесть месяцев позже формального подписания договора.

Чтобы произвести автомобили, MagnetoCorp должна нанять 1000 сотрудников не менее, чем
на полгода. Из-за этого у компании возникает краткосрочный кассовый разрыв - каждый из этих
шести месяцев компания должна будет платить 5 млн долларов США в виде зарплаты своим сотрудникам.
**Коммерческие ценные бумаги** призваны помочь MagnetoCorp закрыть эту краткосрочную потребность
в финансировании в расчете на поступления после того, как Daintree начнет рассчитываться
за поставки автомобилей "Модель D".

Уже к концу мая MagnetoCorp необходимо найти 5M USD на зарплату сотрудников, нанятых
с 1 мая. Для этого компания выпускает коммерческие ценные бумаги с номиналом 5M USD
и сроком погашения 6 месяцев (до начала поступления денег от покупателя).
Банк DigiBank полагает MagnetoCorp кредитоспособной и поэтому не требует по этим
бумагам такой уж высокой премии сверх базовой банковской ставки 2% (по базовой ставке 5M USD
через 6 месяцев оцениваются как 4.95M USD сегодня). Поэтому банк покупает 6-месячные
коммерческие ценные бумаги MagnetoCorp за 4.9M USD - с небольшим дисконтом по сравнению
с их стоимостью в 4.9M USD. DigiBank уверенно ожидает, что через 6 месяцев 5M USD будут
погашены MagnetoCorp, принеся банку 10K USD прибыли за повышенный риск этих бумаг.
Дополнительные 10K USD означают, что банк получает доходность 2.4% - намного лучше,
чем безрисковые 2%.


В конце июня MagnetoCorp производит новый выпуск коммерческих ценных бумаг на 5M USD
для выплаты июньской зарплаты, и этот выпуск приобретает фонд BigFund за 4.9M USD.  
Коммерческое состояние компании не изменилось значительно по сравнению с маем, поэтому
фонд оценил коммерческие ценные бумаги примерно во столько же, что и банк DigiBank в
мае.

В каждый из последующих месяцев MagnetoCorp может производить очередной выпуск
коммерческих ценных бумаг для финансирования своих обязательств по зарплате, и эти
выпуски могут быть приобретены как банком DigiBank, так и любым другим участником
коммерческой сети PaperNet - фондом Bigfund, фондом HedgeMatic или брокерской компанией
BrokerHouse. В зависимости от двух факторов - ключевой ставки центрального банка и уровня
риска MagnetoCorp, цена бумаг, которую платят эти организации, может изменяться. Уровень
риска MagnetoCorp при этом зависит от ряда других факторов - таких, как объем производства
автомобилей "Модель D" и кредитоспособности компании MagnetoCorp, выраженной в рейтинге,
который присваивает ей рейтинговое агентство RateM.

Роли организаций, которые они выполняют в сети PaperNet различаются: MagnetoCorp выпускает
ценные бумаги, DigiBank, BigFund, HedgeMatic и BrokerHouse торгуют ценными бумагами,
а RateM присваивает рейтинг.
Организации с похожей ролью, такие как DigiBank, Bigfund, HedgeMatic и
BrokerHouse, конкурируют друг с другом. Организации с различающимися ролями - не обязательно,
но все же могут иметь конкурирующие интересы в бизнесе - так, например, MagnetoCorp
заинтересована в более высоком рейтинге для своих бумаг, чтобы продавать их по более
высокой цене, в то время как банк DigiBank от низкого рейтинга мог бы выигрывать, приобретая
бумаги MagnetoCorp по более низкой цене. Как видите, даже такая, казалось бы, простая сеть,
как PaperNet может порождать сложные взаимоотношения доверия. Блокчейн может помочь  
установить доверие между организациями - конкурентами. В частности, Fabric обладает для
этого средствами отражения даже очень детальной структуры отношений доверия.

Давайте пока отвлечемся от истории с MagnetoCorp на минуту, и приступим к
разработке клиентских приложений и смарт-контрактов в PaperNet. Эти приложения и
смарт-контракты, отражающие отношения доверия между организациями-участниками, используются
в PaperNet для эмиссии, купли/продажи и погашения коммерческих ценных бумаг.
К роли рейтингового агентства RateM мы вернемся чуть позже. 

<!--- Licensed under Creative Commons Attribution 4.0 International License
https://creativecommons.org/licenses/by/4.0/ -->
