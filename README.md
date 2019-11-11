# Пример передачи ПТУ. Выгрузка из 1С:
```bsl
Типы = Новый Структура;
Типы.Вставить("ПТУ", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "ПТУ"));
Типы.Вставить("Организация", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "Организация"));
Типы.Вставить("Документ", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "Документ"));
Типы.Вставить("Товар", Типы.ПТУ.Свойства.Получить("Товар").Тип);
Типы.Вставить("ГТД", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "ГТД"));
Типы.Вставить("Производитель", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "Производитель"));
Типы.Вставить("Серия", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "Серия"));
Типы.Вставить("Цена", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "Цена"));
Типы.Вставить("СертификатСоответствия", ФабрикаXDTO.Тип("http://www.santens.ru/exchange", "СертификатСоответствия"));

ПТУ = ФабрикаXDTO.Создать(Типы.ПТУ);
ПТУ.Дата = ТекущаяДата(); ПТУ.Номер = 08798790;

ПТУ.Продавец = ФабрикаXDTO.Создать(Типы.Организация);
ПТУ.Покупатель = ФабрикаXDTO.Создать(Типы.Организация);
ПТУ.Грузополучатель = ФабрикаXDTO.Создать(Типы.Организация);
ПТУ.Продавец.ИНН = 534523453; ПТУ.Продавец.КПП = 234234;
ПТУ.Продавец.Наименование = "Полное юридическое наименование организации";
ПТУ.Покупатель.ИНН = 3242342343; ПТУ.Покупатель.КПП = 2454534532;
ПТУ.Покупатель.Наименование = "Полное юридическое наименование организации";
ПТУ.Грузополучатель.ИНН = 234567; ПТУ.Грузополучатель.КПП = 9798798;
ПТУ.Грузополучатель.Наименование = "Полное юридическое наименование организации";

ПТУ.СчетФактура = ФабрикаXDTO.Создать(Типы.Документ);
ПТУ.СчетФактура.Номер = 87698769; ПТУ.СчетФактура.Дата = ТекущаяДата();

Товары = ПТУ.ПолучитьСписок(Типы.ПТУ.Свойства.Получить("Товар"));

Товар = ФабрикаXDTO.Создать(Типы.Товар);
Товар.УникальныйИдентификатор = XMLСтрока(Новый УникальныйИдентификатор);
Товар.ЗаказОснование = ФабрикаXDTO.Создать(Типы.Документ);
Товар.ЗаказОснование.Номер = 879879;
Товар.ЗаказОснование.Дата = ТекущаяДата()-768768;
Товар.Наименование = "Таблетки от болезни 30мг";
Товар.ГТД = ФабрикаXDTO.Создать(Типы.ГТД);
Товар.ГТД.Номер = "879879/9879698/64545676";
Товар.ГТД.Страна = "EN";
Товар.Производитель = ФабрикаXDTO.Создать(Типы.Производитель);
Товар.Производитель.Наименование = "Gorbin&Berk";
Товар.Производитель.Страна = "EN";
Товар.Серия = ФабрикаXDTO.Создать(Типы.Серия);
Товар.Серия.Код = "87987-ВОРА_13";
Товар.Серия.ДатаИзготовления = ТекущаяДата()-8768;
Товар.Серия.ДатаИстеченияСрокаГодности = ТекущаяДата()+87687;
Товар.Код = "МТ-987987ф";
Товар.Количество = 876;
Товар.СтавкаНДС = 10;
Товар.Цена = ФабрикаXDTO.Создать(Типы.Цена);
Товар.Цена.Значение = 768.23; Товар.Цена.ВключаетНДС = Истина;
Товар.Цена.ЦенаГосРеестра = 710;
Товар.Цена.ЦенаПроизводителя = 725.13;
Товар.Штрихкод.Добавить(46787898799); Товар.Штрихкод.Добавить(46787898749); Товар.Штрихкод.Добавить(46787834399);
СертификатыСоответствия = Товар.ПолучитьСписок(Типы.Товар.Свойства.Получить("СертификатСоответствия"));
СертификатСоответствия = ФабрикаXDTO.Создать(Типы.СертификатСоответствия);
СертификатСоответствия.Безсрочный = Ложь;
СертификатСоответствия.ДатаВыдачи = ТекущаяДата()-45333;
СертификатСоответствия.ДатаНачалаДействия = ТекущаяДата()-45033;
СертификатСоответствия.ДатаОкончанияДействия = ТекущаяДата()+45333;
СертификатСоответствия.Декларант = "Завод по производству таблеток";
СертификатСоответствия.ОрганВыдачи = "МУП ЖРЕП ВНО ПСО г.Москва";
СертификатСоответствия.ОрганРегистрации = "Регистрационный отдел №789 г.Москва";
СертификатСоответствия.РегистрационныйНомер = "АБ-76897689-98709/2019";
СертификатыСоответствия.Добавить(СертификатСоответствия);
СертификатыСоответствия.Добавить(СертификатСоответствия);
Товары.Добавить(Товар);Товары.Добавить(Товар);

Запись = Новый ЗаписьXML; Запись.УстановитьСтроку();
ФабрикаXDTO.ЗаписатьXML(Запись,ПТУ,"ПТУ");
Стр = Запись.Закрыть();
```
```bsl
<ПТУ xmlns="http://www.santens.ru/exchange" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" Номер="8798790" Дата="2019-10-30">
	<Продавец ИНН="534523453" КПП="234234">Полное юридическое наименование организации</Продавец>
	<Покупатель ИНН="3242342343" КПП="2454534532">Полное юридическое наименование организации</Покупатель>
	<Грузополучатель ИНН="234567" КПП="9798798">Полное юридическое наименование организации</Грузополучатель>
	<СчетФактура Номер="87698769" Дата="2019-10-30"/>
	<Товар УникальныйИдентификатор="88932106-d217-43c3-acfc-68beaa154919">
		<Код>МТ-987987ф</Код>
		<Наименование>Таблетки от болезни 30мг</Наименование>
		<Серия Код="87987-ВОРА_13">
			<ДатаИстеченияСрокаГодности>2019-10-31</ДатаИстеченияСрокаГодности>
			<ДатаИзготовления>2019-10-30</ДатаИзготовления>
		</Серия>
		<Производитель Страна="EN">Gorbin&amp;Berk</Производитель>
		<Штрихкод>46787898799</Штрихкод>
		<Штрихкод>46787898749</Штрихкод>
		<Штрихкод>46787834399</Штрихкод>
		<ЗаказОснование Номер="879879" Дата="2019-10-21"/>
		<Количество>876</Количество>
		<СтавкаНДС>10</СтавкаНДС>
		<Цена ВключаетНДС="true" Значение="768.23">
			<ЦенаГосРеестра>710</ЦенаГосРеестра>
			<ЦенаПроизводителя>725.13</ЦенаПроизводителя>
		</Цена>
		<ГТД Страна="EN">879879/9879698/64545676</ГТД>
		<СертификатСоответствия Безсрочный="false">
			<РегистрационныйНомер>АБ-76897689-98709/2019</РегистрационныйНомер>
			<ОрганРегистрации>Регистрационный отдел №789 г.Москва</ОрганРегистрации>
			<ОрганВыдачи>МУП ЖРЕП ВНО ПСО г.Москва</ОрганВыдачи>
			<Декларант>Завод по производству таблеток</Декларант>
			<ДатаВыдачи>2019-10-29</ДатаВыдачи>
			<ДатаНачалаДействия>2019-10-29</ДатаНачалаДействия>
			<ДатаОкончанияДействия>2019-10-30</ДатаОкончанияДействия>
		</СертификатСоответствия>
		<СертификатСоответствия Безсрочный="false">
			<РегистрационныйНомер>АБ-76897689-98709/2019</РегистрационныйНомер>
			<ОрганРегистрации>Регистрационный отдел №789 г.Москва</ОрганРегистрации>
			<ОрганВыдачи>МУП ЖРЕП ВНО ПСО г.Москва</ОрганВыдачи>
			<Декларант>Завод по производству таблеток</Декларант>
			<ДатаВыдачи>2019-10-29</ДатаВыдачи>
			<ДатаНачалаДействия>2019-10-29</ДатаНачалаДействия>
			<ДатаОкончанияДействия>2019-10-30</ДатаОкончанияДействия>
		</СертификатСоответствия>
	</Товар>
	<Товар УникальныйИдентификатор="88932106-d217-43c3-acfc-68beaa154919">
		<Код>МТ-987987ф</Код>
		<Наименование>Таблетки от болезни 30мг</Наименование>
		<Серия Код="87987-ВОРА_13">
			<ДатаИстеченияСрокаГодности>2019-10-31</ДатаИстеченияСрокаГодности>
			<ДатаИзготовления>2019-10-30</ДатаИзготовления>
		</Серия>
		<Производитель Страна="EN">Gorbin&amp;Berk</Производитель>
		<Штрихкод>46787898799</Штрихкод>
		<Штрихкод>46787898749</Штрихкод>
		<Штрихкод>46787834399</Штрихкод>
		<ЗаказОснование Номер="879879" Дата="2019-10-21"/>
		<Количество>876</Количество>
		<СтавкаНДС>10</СтавкаНДС>
		<Цена ВключаетНДС="true" Значение="768.23">
			<ЦенаГосРеестра>710</ЦенаГосРеестра>
			<ЦенаПроизводителя>725.13</ЦенаПроизводителя>
		</Цена>
		<ГТД Страна="EN">879879/9879698/64545676</ГТД>
		<СертификатСоответствия Безсрочный="false">
			<РегистрационныйНомер>АБ-76897689-98709/2019</РегистрационныйНомер>
			<ОрганРегистрации>Регистрационный отдел №789 г.Москва</ОрганРегистрации>
			<ОрганВыдачи>МУП ЖРЕП ВНО ПСО г.Москва</ОрганВыдачи>
			<Декларант>Завод по производству таблеток</Декларант>
			<ДатаВыдачи>2019-10-29</ДатаВыдачи>
			<ДатаНачалаДействия>2019-10-29</ДатаНачалаДействия>
			<ДатаОкончанияДействия>2019-10-30</ДатаОкончанияДействия>
		</СертификатСоответствия>
		<СертификатСоответствия Безсрочный="false">
			<РегистрационныйНомер>АБ-76897689-98709/2019</РегистрационныйНомер>
			<ОрганРегистрации>Регистрационный отдел №789 г.Москва</ОрганРегистрации>
			<ОрганВыдачи>МУП ЖРЕП ВНО ПСО г.Москва</ОрганВыдачи>
			<Декларант>Завод по производству таблеток</Декларант>
			<ДатаВыдачи>2019-10-29</ДатаВыдачи>
			<ДатаНачалаДействия>2019-10-29</ДатаНачалаДействия>
			<ДатаОкончанияДействия>2019-10-30</ДатаОкончанияДействия>
		</СертификатСоответствия>
	</Товар>
</ПТУ>
```
```bsl
Книга = ПолучитьCOMОбъект("C:\Users\user\Desktop\Каталог.xlsx");
Карты = Новый Структура("Каталог,ШтрихКоды");
Для Каждого Карта Из Карты Цикл
  Если Книга.XMLMaps(Карта.Ключ).IsExportable Тогда
    XML = Неопределено;
    Если Не Книга.XMLMaps(Карта.Ключ).ExportXml(XML) Тогда
      Карты.Вставить(Карта.Ключ,XML);
    КонецЕсли;
  КонецЕсли;
КонецЦикла;
Книга = Книга.Close(Ложь);

Чтение = Новый ЧтениеXML;
Пакет = ФабрикаXDTO.Пакеты.Получить("СантенсKаталогТоваров");
Для Каждого Карта Из Карты Цикл
  Если ЗначениеЗаполнено(Карта.Значение) Тогда
    Чтение.УстановитьСтроку(Карта.Значение);
    Карты.Вставить(Карта.Ключ,ФабрикаXDTO.ПрочитатьXML(Чтение
    ,Пакет.КорневыеСвойства.Получить(Карта.Ключ).Тип));
  КонецЕсли;
КонецЦикла;

```
