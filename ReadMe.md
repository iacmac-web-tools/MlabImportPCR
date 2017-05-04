![IACMAC](http://www.iacmac.ru/iacmac/img/head3b.jpg) Руководство пользователя
---

#Как импортировать в Mlab данные ПЦР-маркеров

В данном руководстве будут описываться шаги по правильному импорту данных ПЦР-маркеров, в базу данных **Mlab** с помощью программы **MlabReporter**. Общая последовательность действий следующая:

1. Подготовка файла для импорта
2. Импорт файла
3. Проверка корректности импорта

[TOC]

## Подготовка файла для импорта
Чтобы импортировать данные нам нужно сделать файл **CSV** с особой структурой. Пример такого файла в **Excel** выглядит так:

![001](./img/001.png)

Если его открыть в **Блокноте**, он будет выглядеть так:

![002](./img/002.png)

>**Примечание**: Пример файла для заполнения можно получить из программы **MlabReporter**, нажав на кнопку **Получить пример файла**.
![002-1](./img/002-1.png)

###Требования к файлу

1. Первый столбец должен всегда определяет идентификатор штамма к которому будут относиться эти параметры. Идентификатором может выступать **Номер НИИАХ**, **Музейный номер**, **ROID**. Рекомендуется называть первый столбец согласно тому, что он содержит, чтобы потом не было путаницы.

2. Одна строка - один штамм.

3. После идентификатора идут столбцы с параметрами. Количество параметров может быть произвольным, как и их порядок. Но крайне рекомендуется, чтобы названия этих параметров были стандартизированы. На данный момент в **Mlab** используются следующие параметры:

	- ESBL_DDST
	- ESBL_MIC
	- MBL_DDST_DPA
	- MBL_DDST_EDTA
	- Carba_NP
	- ROSCO_Carb
	- PCR_VIM
	- PCR_IMP
	- PCR_NDM
	- PCR_OXA-48
	- PCR_KPC
	- PCR_OXA-40
	- PCR_OXA-23
	- PCR_OXA-58
	- PCR_OXA-51
	- PCR_GES
	- PCR_mecA
	- CIM
	- MHT
	- Disk_IMI
	- Disk_MER
	- Disk_ERT
	- Disk_FOX
	- ID_OPT
	- ID_Aggl
	- ID_Bа_0.04

4. На пересечении строк и столбцов должны стоять значения этих параметров. Допустимые значения представлены в таблице ниже:
	- **ESBL_DDST**: Positive / Negative
	- **ESBL_MIC**: Positive / Negative / Doubtful
	- **MBL&#95;DDST&#95;DPA**: Positive / Negative / Doubtful|
	- **MBL&#95;DDST&#95;EDTA**: Positive / Negative / Doubtful
	- **Carba_NP**: Positive / Negative / Doubtful
	- **ROSCO_Carb**: Positive / Negative / Doubtful
	- **PCR_VIM**: Positive / Negative
	- **PCR_IMP**: Positive / Negative
	- **PCR_NDM**: Positive / Negative
	- **PCR_OXA-48**: Positive / Negative
	- **PCR_KPC**: Positive / Negative
	- **PCR_OXA-40**: Positive / Negative
	- **PCR_OXA-23**: Positive / Negative
	- **PCR_OXA-58**: Positive / Negative
	- **PCR_OXA-51**: Positive / Negative
	- **PCR_GES**: Negative / GES-1-like / GES-2-like / GES-5-like
	- **PCR_mecA**: Positive / Negative
	- **CIM**: Positive / Negative / Doubtful
	- **MHT**: Positive / Negative / Doubtful
	- **ID_OPT**: Positive / Negative / Doubtful
	- **ID_Aggl**: Positive / Negative / Doubtful / group A / group B / group C / group D / group F / group G
	- **ID&#95;Bа&#95;0.04**: Positive / Negative / Doubtful

5. Лишних строк и столбцов быть не должно.

6. Перед и после значений параметров не должно быть лишних пробелов.

7. Файл CSV должен быть сохранен в кодировке **Windows 1251**, разделители полей - **точка с запятой**.

> **Примечание:** Формат хранения данных ПЦР-маркеров по сути является простым текстом. Поэтому очень важно, чтобы соблюдалось единообразие при заполнении. Старайтесь использовать только те значения, которые указаны выше. Помните - программа запишет ровно то, что ей сказали.

### Попробуем сформировать сам документ
1. Сделаем в **Excel** нужную нам табличку.
![003](./img/003.png)

2. На всякий случай сделаем замены для вероятных **positive** и **negative** на **Positive** и **Negative** соответственно. (Комбинация клавиш **Ctrl+H**)
![004](./img/004.png)

3. На всякий случай удалим лишние столбцы
![005](./img/005.png)

4. На всякий случай удалим лишние строки
![006](./img/006.png)

5. Теперь можно сохранить файл в формате CSV. Для этого выбираем **Файл** - **Сохранить как** и в поле **Тип файла** выбираем **CSV (разделители - запятые)**.
![007](./img/007.png)

Появится сообщение *В файле выбранного типа может быть сохранен только текущий лист*, нажимаем **ОК**.

Потом появится сообщение *Файл может содержать возможности, несовместимые с форматом CSV (разделители запятые). Сохранить книгу в этом формате?*, нажимаем **Да**.

После этого закрываем **Excel** и на вопрос *Сохранить изменения в файле* нажимаем **Не сохранять**.

6. Чтобы проверить правильность файла откроем его в блокноте. Вот так он должен выглядеть:
![008](./img/008.png)
Если файл выглядит вот так:
![009](./img/009.png)
Или вот так:
![010](./img/010.png)

**ТО ЭТО НЕПРАВИЛЬНО И НУЖНО УДАЛИТЬ ЛИШНИЕ СТРОКИ/СТОЛБЦЫ**

## Импорт файла
Для импорта файла ПЦР-маркеров используется программа **MlabReporter**. Окно импорта выглядит следующим образом:
![011](./img/011.png)

Общий порядок действий по импорту выглядит следующим образом:

### Загрузка файла
Загружаем файл в программу. Для этого нажимаем кнопку **Загрузить CSV**. Если файл был сформирован правильно, то после окончания закрузки окно программы будет выглядеть следующим образом:
![012](./img/012.png)

Если после загрузки программы таблица выглядит так:
![013](./img/013.png)
или вот так:
![014](./img/014.png)
или даже так:
![015](./img/015.png)
то значит, что файл был сформирован неправильно и его нужно переделать.

### Загрузка данных из базы
Теперь нужно, чтобы программа нашла интересующие нас штаммы в базе данных. Для этого мы выставляем в выпадающем списке **Первый столбец определяет**, что именно содержится в первом столбце нашего файла. В данном примере это **Номер НИИАХ**. После этого нажимаем кнопку **Загрузить ROID**. Программа получит данные и ее окно примет следующий вид:
![016](./img/016.png)
Обратите внимание, что обновились столбцы **ROID**, **MusNum**, **IacNum**, **Сравнение**. Они показывают какой именно штамм удалось найти в базе данных по первому столбцу нашего файла. Эти столбцы отображают следующее:

- **ROIDNum** - Внутренний уникальный идентификатор штамма в базе данных
- **MusNum** - музейный номер
- **IacNum** - Номер НИИАХ
- **Сравнение** - Результат сопоставления параметров из файлов с тем, что хранится в базе. Возможно несколько значений:
	* **New** - в базе данных отсутствовали значения параметров, в файле параметры есть.
	* **Equals** - значения параметров в базе данных и в файле полностью совпадают.
	* **Update** - в базе данных уже есть параметры и их набор отличается от того, что есть в файле. 
	* **Conflict** - в базе данных есть параметры, которые противоречат параметрам, которые в файле (например, в базе PCR_VIM = Positive, в файле PCR_VIM = Negative)

>**Примечание**: Внимательно посмотрите, действительно ли программа нашла те штаммы, которые вы хотите обновить. После записи действие нельзя будет отменить!

В нашем случае все прошло хорошо, и мы нашли все штаммы из нашего файла. При этом для этих штаммов отсутствуют ранее записанные данные ПЦР-маркеров. Мы можем посмотреть, корректно ли программа распознала наши данные. Для этого выделим какую-либо строку таблицы и мы увидим распарсенные значения параметров, которые будут записаны в базу:
![017](./img/017.png)
либо вот так
![018](./img/018.png)

Если же в базе данных уже были данные ПЦР-маркеров, то картина будет следующая:
![019](./img/019.png)
или такая:
![020](./img/020.png)

Если же после нажатия кнопки столбцы **ROIDNum**, **MusNum**, **IacNum** остались пустые, значит что программе не удалось найти соответствие в базе данных штаммам из файла. Выглядит это вот так:

![021](./img/021.png)

В этом случае:

- проверьте, правильно ли выставлено значение выпадающего списка **Первый столбец определяет**.
- проверьте, правильные ли номера стоят в первом столбце файла.

### Запись данных в базу.

Теперь мы подошли к самому ответственному моменту - записи данных в базу. Существует две возможности записи: с обновлением или с заменой. 

![022](./img/022.png)

В чем их различие?

- **Записать все с Заменой** - полностью удаляет содержимое параметров в базе данных и записывает вместо них параметры из файла
- **Записать все с Обновлением** - берет параметры из базы, объединяет их с параметрами из файла, удаляет дубликаты и только после этого записывает объединенные параметры в базу.

Здесь никаких рекомендаций быть не может, каждый решает сам, что именно ему нужно. Хочется только обратить внимание, что по нажатии кнопки будут записаны все строки файла. Если требуется часть файла записать с обновлением, а часть с заменой - разбейте исходный файл на два.

После того, как данные будут записано, в столбце **Сравнение** появится статус **Written in db**.

## Проверка корректности импорта
Проверить, все ли корректно записалось можно двумя способами:

- После процедуры записи повторно нажать кнопку **Загрузить ROID** и посмотреть, что появится на панели **Параметры**.
- В самом Mlab открыть интересующий штамм и посмотреть что там у него. 

