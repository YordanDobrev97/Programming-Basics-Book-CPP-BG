# Глава 9.1. Задачи за шампиони – част I

В настоящата глава ще предложим на читателя няколко малко **по-трудни задачи**, които имат за цел развиване на **алгоритмични умения** и усвояване на **програмни техники** за решаване на задачи с по-висока сложност.

## По-сложни задачи върху изучавания материал

Ще решим заедно няколко задачи по програмиране, които обхващат изучавания в книгата учебен материал, но по трудност надвишават обичайните задачи от приемните изпити в СофтУни. Ако искате да **станете шампиони по основи на програмирането**, ви препоръчваме да тренирате решаване на подобни по-сложни задачи, за да ви е лесно на изпитите.


## Задача: пресичащи се редици

Имаме две редици:
 - **редица на Трибоначи** (по аналогия с редицата на Фибоначи), където всяко число е **сумата от предните три** (при дадени начални три числа)
 - редица, породена от **числова спирала**, дефинирана чрез обхождане като спирала (дясно, долу, ляво, горе, дясно, долу, ляво, горе и т.н.) на матрица от числа, стартирайки от нейния център с дадено начално число и стъпка на увеличение, със записване на текущите числа в редицата всеки път, когато направим завой

Да се напише програма, която намира първото число, което се появява **и в двете така дефинирани редици**.

### Пример

Нека **редицата на Трибоначи** да започне с **1**, **2** и **3**. Това означава, че **първата редица** ще съдържа числата 1, 2, 3, 6, 11, 20, 37, 68, 125, 230, 423, 778, 1431, 2632, 4841, 8904, 16377, 30122, 55403, 101902 и т.н.

Същевременно, нека **числата в спиралата** да започнат с **5** и спиралата да се увеличава с **2** на всяка стъпка.

<img src="/assets/chapter-9-images/01.Crossing-sequences-01.png" style="float: right; height: 250px;" />

Тогава **втората редица** ще съдържа числата 5, 7, 9, 13, 17, 23, 29, 37 и т.н. Виждаме, че **37** е първото число, което се среща в редицата на Трибоначи и в спиралата и това е търсеното решение на задачата.

### Входни данни

Входните данни трябва да бъдат прочетени от конзолата.
 * На първите три реда от входа ще се подават **три цели числа**, представляващи **първите три числа** в редицата на Трибоначи, положителни ненулеви числа, сортирани в нарастващ ред. 
 * На следващите два реда от входа, ще се подават **две цели числа**, представляващи **първото число** и **стъпката** за всяка клетка на матрицата за спиралата от числа. Числата, описващи спиралата, са положителни ненулеви.

Входните данни винаги ще бъдат валидни и винаги ще са в описания формат. Няма нужда да се проверяват.

### Изходни данни

Резултатът трябва да бъде принтиран на конзолата.

На единствения ред от изхода трябва да принтирате **най-малкото число, което се среща и в двете последователности**. Ако няма число в **диапазона** [**1 … 1 000 000**], което да се среща и в двете последователности, принтирайте "**No**".

### Ограничения

* Всички числа във входа ще бъдат в диапазона [**1 … 1 000 000**].
* Позволено работно време за програмата: 0.3 секунди.
* Позволена памет: 16 MB.

### Примерен вход и изход

| Вход | Изход  | Вход | Изход | Вход | Изход |
| ------ | -------- | ------ | ------------ | ------ | -------- |
|1<br>2<br>3<br>5<br>2<br>|37|13<br>25<br>99<br>5<br>2|13|99<br>99<br>99<br>2<br>2|No|


| Вход | Изход  | Вход | Изход      |
| ------ | ------- | ------ | ------------ |
|1<br>1<br>1<br>1<br>1|1|1<br>4<br>7<br>23<br>3|23|

### Насоки и подсказки

Задачата изглежда доста сложна и затова ще я разбием на по-прости подзадачи.

#### Обработване на входа

Първата стъпка от решаването на задачата е да прочетем и обработим входа. Входните данни се състоят от **5 цели числа**: **3** за редицата на Трибоначи и **2** за числовата спирала.

![](/assets/old-images/chapter-9-images/01.Crossing-sequences-02.png)

След като имаме входните данни, трябва да помислим как ще генерираме числата в двете редици.

#### Генериране на редица на Трибоначи

За редицата на Трибоначи всеки път ще **събираме предишните три стойности** и след това ще отместваме стойностите на тези числа (трите предходни) с една позиция напред в редицата, т.е. стойността на първото трябва да приеме стойността на второто и т.н. Когато сме готови с числото, ще запазваме стойността му в **масив**. Понеже в условието на задачата е казано, че числата в редиците не превишават 1,000,000, можем да спрем генерирането на тази редица именно при 1,000,000.

![](/assets/old-images/chapter-9-images/01.Crossing-sequences-03.png)

#### Генериране на числова спирала

Трябва да измислим **зависимост** между числата в числовата спирала, за да можем лесно да генерираме всяко следващо число, без да се налага да разглеждаме матрици и тяхното обхождане. Ако разгледаме внимателно картинката от условието, можем да забележим, че **на всеки 2 "завоя" в спиралата числата, които прескачаме, се увеличават с 1**, т.е. от *5 до 7* и от *7 до 9* не се прескача нито 1 число, а директно **събираме със стъпката** на редицата. От *9 до 13* и от *13 до 17* прескачаме едно число, т.е. събираме два пъти стъпката. От *17 до 23* и от *23 до 29* прескачаме две числа, т.е. събираме три пъти стъпката и т.н.

Така виждаме, че при първите две имаме **`последното числото + 1 * стъпката`**, при следващите две събираме с **`2 * стъпката`** и т.н.
Всеки път, когато искаме да стигнем до следващото число от спиралата, ще трябва да извършваме такива изчисления.


![](/assets/old-images/chapter-9-images/01.Crossing-sequences-04.png)

Това, за което трябва да се погрижим, е **на всеки две числа нашият множител** (нека го наречем "коефициент") **да се увеличава с 1** (**`spiralStepMul++`**), което може да се постигне с проста проверка (**`spiralCount % 2 == 0`**). Целият код от генерирането на спиралата в **масив** е даден по-долу.

![](/assets/old-images/chapter-9-images/01.Crossing-sequences-05.png)

#### Намиране на общо число за двете редици

След като сме генерирали числата и в двете редици, можем да пристъпим към обединението им и изграждането на крайното решение. Как ще изглежда то? За **всяко от числата** в едната редица (започвайки от по-малкото) ще проверяваме дали то съществува в другата. Първото число, което отговаря на този критерий ще бъде **отговорът** на задачата.

Търсенето във втория масив ще направим **линейно**, а за по-любопитните ще оставим да си го оптимизират, използвайки техниката наречена **двоично търсене**, тъй като вторият масив се генерира сортиран, т.е. отговаря на изискването за прилагането на този тип търсене. Кодът за намиране на нашето решение ще изглежда така: 

![](/assets/old-images/chapter-9-images/01.Crossing-sequences-06.png)

Решението на задачата използва масиви за запзване на стойностите. Масивите не са необходими за решаването на задачата. Съществува **алтернативно решение**, което генерира числата и работи директно с тях, вместо да ги записва в масив. Можем на **всяка стъпка** да проверяваме дали **числата от двете редици съвпадат**. Ако това е така, ще принтираме на конзолата числото и ще прекратим изпълнението на нашата програма. В противен случай, ще видим текущото число на **коя редица е по-малко и ще генерираме следващото, там където "изоставаме"**. Идеята е, че **ще генерираме числа от редицата, която е "по-назад"**, докато не прескочим текущото число на другата редица и след това обратното, а ако междувременно намерим съвпадение, ще прекратим изпълнението.

![](/assets/old-images/chapter-9-images/01.Crossing-sequences-07.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/518#0](https://judge.softuni.bg/Contests/Practice/Index/518#0).


## Задача: магически дати

Дадена е **дата** във формат "**дд-мм-гггг**", напр. 17-04-2018. Изчисляваме **теглото на тази дата**, като вземем всичките ѝ цифри, умножим всяка цифра с останалите след нея и накрая съберем всички получени резултати. В нашия случай имаме 8 цифри: **17032007**, така че теглото е  **`1*7 + 1*0 + 1*3 + 1*2 + 1*0 + 1*0 + 1*7`** **+** **`7*0 + 7*3 + 7*2 + 7*0 + 7*0 + 7*7`** **+** **`0*3 + 0*2 + 0*0 + 0*0 + 0*7`** **+** **`3*2 + 3*0 + 3*0 + 3*7`** **+** **`2*0 + 2*0 + 2*7`** **+** **`0*0 + 0*7`** **+** **`0*7`** = **144**.

Нашата задача е да напишем програма, която намира всички **магически дати - дати между две определени години (включително), отговарящи на дадено във входните данни тегло**. Датите трябва да бъдат принтирани в нарастващ ред (по дата) във формат "**дд-мм-гггг**". Ще използваме само валидните дати в традиционния календар (високосните години имат 29 дни през февруари).

### Входни данни

Входните данни трябва да бъдат прочетени от конзолата. Състоят се от 3 реда:

*	Първият ред съдържа цяло число: **начална година**.
*	Вторият ред съдържа цяло число: **крайна година**.
*	Третият ред съдържа цяло число: **търсеното тегло** за датите.

Входните данни винаги ще бъдат валидни и винаги ще са в описания формат. Няма нужда да се проверяват.

### Изходни данни

Резултатът трябва да бъде принтиран на конзолата, като последователни дати във **формат "дд-мм-гггг"**, подредени по дата в нарастващ ред. Всеки низ трябва да е на отделен ред. В случай, че няма съществуващи магически дати, да се принтира "**No**".

### Ограничения

* Началната и крайната година са цели числа в периода [**1900 - 2100**].
* Магическото тегло е цяло число в диапазона [**1 … 1000**].
* Позволено работно време за програмата: 0.25 секунди.
* Позволена памет: 16 MB.

### Примерен вход и изход

| Вход | Изход      | Вход | Изход      |
|------|------------|------|------------|
|2007<br>2007<br>144|17-03-2007<br>13-07-2007<br>31-07-2007|2003<br>2004<br>1500<br>|No|

| Вход | Изход      | Вход | Изход      |
|------|------------|------|------------|
|2012<br>2014<br>80|09-01-2013<br>17-01-2013<br>23-03-2013<br>11-07-2013<br>01-09-2013<br>10-09-2013<br>09-10-2013<br>17-10-2013<br>07-11-2013<br>24-11-2013<br>14-12-2013<br>23-11-2014<br>13-12-2014<br>31-12-2014|2011<br>2012<br>14<br>|01-01-2011<br>10-01-2011<br>01-10-2011<br>10-10-2011|

### Насоки и подсказки

Започваме от входните данни. В случая имаме **3 цели числа**, които трябва да се прочетат от конзолата, като с това се изчерпва въвеждането и обработването на входа за задачата.

Разполагайки с началната и крайната година, е хубаво да разберем как ще минем през всяка дата, без да се объркваме от това колко дена има в месеца и дали е високосна година и т.н.

#### Обхождане на всички дати

За обхождането ще се възползваме от функционалността, която ни дава **`DateTime`** класът в **C++**. Ще си дефинираме **променлива за началната дата**, което можем да направим, използвайки конструктора, който приема година, месец и ден. Знаем, че годината е началната година, която сме прочели от конзолата, а месеца и деня трябва да са съответно януари и 1-ви. При C++ "конструкторът" на **`DateTime`** приема като първи аргумент годината, като втори аргумент месеца и като трети аргумент деня от месеца:

![](/assets/old-images/chapter-9-images/02.Magic-dates-01.png)

След като имаме началната дата, искаме да направим **цикъл, който се изпълнява, докато не превишим крайната година** (или докато не преминем 31 декември в крайната година, ако сравняваме целите дати), като на всяка стъпка увеличава с по 1 ден.

За да увеличаваме с 1 ден при всяко завъртане, ще използваме метод от **`DateTime` - `.AddDays(…)`**, чрез който ще добавяме по един ден към текущата дата. Методът ще се грижи вместо нас кога трябва да прескочи в следващия месец, колко дни има даден месец и всичко около високосните години.

![](/assets/old-images/chapter-9-images/02.Magic-dates-02.png)

***Внимание***: тъй като методът **`.AddDays(…)`** връща "новата" дата, е важно да имаме присвояване на резултата, а не само извикване на метода!

В крайна сметка нашият цикъл може да изглежда по следния начин:

![](/assets/old-images/chapter-9-images/02.Magic-dates-03.png)

***Забележка***: може да постигнем същия резултат с **`for` цикъл**, инициализацията на датата отива в първата част на **`for`**, условието се запазва, а стъпката е увеличаването с 1 ден.

#### Пресмятане на теглото

Всяка дата се състои от точно **8 символа (цифри)** - **2 за деня** (**`d1`**, **`d2`**), **2 за месеца** (**`d3`**, **`d4`**) и **4 за годината** (**`d5`** до **`d8`**). Това означава, че всеки път ще имаме едно и също пресмятане и може да се възползваме от това, за **да дефинираме формулата статично** (т.е. да не обикаляме с цикли, реферирайки различни цифри от датата, а да изпишем цялата формула). За да успеем да я изпишем, ще ни трябват **всички цифри от датата** в отделни променливи, за да направим всички нужни умножения. Използвайки операциите деление и взимане на остатък върху отделните компоненти на датата, чрез свойствата **`Day`**, **`Month`** и **`Year`**, можем да извлечем всяка цифра.

![](/assets/old-images/chapter-9-images/02.Magic-dates-04.png)

Нека обясним и един от по-интересните редове тук. Нека вземе за пример взимането на втората цифра от годината (**`d6`**). При нея делим годината на 100 и взимаме остатък от 10. Какво постигаме така? Първо с деленето на 100 отстраняваме последните 2 цифри от годината (пример: **`2018 / 100 = 20`**). С остатъка от деление на 10 взимаме последната цифра на полученото число (**`20 % 10 = 0`**) и така получаваме 0, което е втората цифра на 2018.

Остава да направим изчислението, което ще ни даде магическото тегло на дадена дата. За да **не изписваме всички умножения**, както е показано в примера, ще приложим просто групиране. Това, което трябва да направим, е да умножим всяка цифра с тези, които са след нея. Вместо да изписваме **`d1 * d2 + d1 * d3 + … + d1 * d8`**, може да съкратим този израз до **`d1 * (d2 + d3 + … + d8)`**, следвайки математическите правила за групиране, когато имаме умножение и събиране. Прилагайки същото опростяване за останалите умножения, получаваме следната формула: 

![](/assets/old-images/chapter-9-images/02.Magic-dates-05.png)

#### Отпечатване на изхода

След като имаме пресметнато теглото на дадена дата, трябва **да проверим дали съвпада с търсеното от нас магическо тегло**, за да знаем, дали трябва да се принтира или не. Проверката може да се направи със стандартен **`if`** блок, като трябва да се внимава при принтирането датата да е в правилния формат.

![](/assets/old-images/chapter-9-images/02.Magic-dates-06.png)

За отпечатването на датите имаме два варианта:

* Първият начин е да използваме метода **`.ToString(…)`**, на който можем да **подадем формат на датата**, т.е. дали дните да се изписват с водеща нула или не, дали месеците да се изписват с водещи нули или не, с думи или с цифри, с кратък запис или с пълно име и т.н.

![](/assets/old-images/chapter-9-images/02.Magic-dates-07.png)

* Вторият вариант е да вземем отделните компоненти на датата **`Day`**, **`Month`** и **`Year`**, както направихме при пресмятането, и да си оформим изхода чрез **форматиращ стринг**.

![](/assets/old-images/chapter-9-images/02.Magic-dates-08.png)

***Внимание***: тъй като обхождаме датите от началната година към крайната, те винаги ще бъдат подредени във възходящ ред, както е по условие.

И накрая, ако не сме намерили нито една дата, отговаряща на условията, ще имаме **`false`** стойност във **`found`** променливата и ще можем да отпечатаме **`No`**.

![](/assets/old-images/chapter-9-images/02.Magic-dates-09.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/518#1](https://judge.softuni.bg/Contests/Practice/Index/518#1).


## Задача: пет специални букви

Дадени са две числа: **начало** и **край**. Напишете програма, която **генерира всички комбинации от 5 букви**, всяка измежду множеството **`{'a', 'b', 'c', 'd', 'e'}`**, така че теглото на тези 5 букви да е число в интервала **`[начало … край]`**, включително. Принтирайте ги по азбучен ред, на един ред, разделени с интервал.

**Теглото на една буква** се изчислява по следния начин:

```csharp 
weight('а') = 5;
weight('b') = -12;
weight('c') = 47;
weight('d') = 7;
weight('e') = -32;
```

**Теглото на редицата** от букви **`c1, c2, …, cn`** е изчислено, като се премахват всички букви, които се повтарят (от дясно наляво), и след това се пресметне формулата:

```csharp 
weight(c1c2…cn) = 1 * weight(c1) + 2 * weight(c2) + … + n * weight(cn)
```

**Например**, теглото на **`bcddc`** се изчислява по следния начин: 

Първо **премахваме повтарящите се букви** и получаваме **`bcd`**. След това прилагаме формулата: **`1 * weight('b') + 2 * weight('c') + 3 * weight('d') = 1 * (-12) + 2 * 47 + 3 * 7 = 103`**.

**Друг пример**: **`weight("cadae") = weight("cade") = 1 * 47 + 2 * 5 + 3 * 7 + 4 * (-32) = -50`**.

### Входни данни

Входните данни се четат от конзолата. Състоят се от две числа:
* Числото за **начало**.
* Числото за **край**.

Входните данни винаги ще бъдат валидни и винаги ще са в описания формат. Няма нужда да се проверяват.

### Изходни данни

Резултатът трябва да бъде принтиран на конзолата като поредица от низове, **подредени по азбучен ред**. Всеки низ трябва да бъде отделен от следващия с едно разстояние. Ако теглото на нито един от 5 буквените низове не съществува в зададения интервал, принтирайте "**No**".

### Ограничения

* Числата за **начало** и **край** да бъдат цели числа в диапазона [**-10000 … 10000**].
* Позволено работно време за програмата: 0.25 секунди.
* Позволена памет: 16 MB.

### Примерен вход и изход

| Вход | Изход       | Коментар             |
| ------ | ------------- | ---------------------- |
|40<br>42|bcead bdcea |weight("bcead") = 41<br>weight("bdcea") = 40|

| Вход | Изход         |
| ------ |---------------|
|-1<br>1| bcdea cebda eaaad eaada eaadd eaade eaaed eadaa eadad eadae eadda eaddd eadde eadea eaded eadee eaead eaeda eaedd eaede eaeed eeaad eeada eeadd eeade eeaed eeead|

| Вход | Изход      |
| ------ |------------|
|200<br>300|baadc babdc badac badbc badca badcb badcc badcd baddc bbadc bbdac bdaac bdabc bdaca bdacb bdacc bdacd bdadc bdbac bddac beadc bedac eabdc ebadc ebdac edbac|

| Вход | Изход  |
| ------ | -------- |
|300<br>400| No|

### Насоки и подсказки

Като всяка задача, започваме решението с **прочитане и обработване на входните данни**. В случая имаме **две цели числа**, които можем да обработим с комбинация от методите **`int.Parse(…)`** и **`Console.ReadLine()`**.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-01.png)

В задачата имаме няколко основни момента - **генерирането на всички комбинации** с дължина 5 включващи 5-те дадени букви, **премахването на повтарящите се букви** и **пресмятането на теглото** за дадена вече опростена дума. Отговорът ще се състои от всяка дума, чието тегло е в дадения интервал **`[firstNumber, secondNumber]`**.

#### Генериране на всички комбинации

За да генерираме **всички комбинации с дължина 1** използвайки 5 символа, бихме използвали **цикъл от 0..4**, като всяко число от цикъла ще искаме да отговаря на един символ. За да генерираме **всички комбинации с дължина 2** използвайки 5 символа (т.е. "aa", "ab", "ac", …, "ba", …), бихме направили **два вложени цикъла, всеки обхождащ цифрите от 0 до 4**, като отново ще направим, така че всяка цифра да отговаря на конкретен символ. Тази стъпка ще повторим 5 пъти, така че накрая да имаме 5 вложени цикъла с индекси **`i1`**, **`i2`**, **`i3`**, **`i4`** и **`i5`**.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-02.png)

Имайки всички 5-цифрени комбинации, трябва да намерим начин да "превърнем" петте цифри в дума с буквите от '**a**' до '**e**'. Един от начините да направим това е, като си **предефинираме прост стринг съдържащ буквите**, които имаме

![](/assets/old-images/chapter-9-images/03.Five-special-letters-03.png)

и **за всяка цифра взимаме буквата от конкретната позиция**. По този начин числото **00000** ще стане **"aaaaa"**, числото **02423** ще стане **"acecd"**. Можем да направим стринга от 5 букви по следния начин.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-04.png)

***Друг начин***: можем да преобразуваме цифрите до букви, използвайки подредбата им в **ASCII таблицата**. Изразът **`'а' + i`** ще ни даде резултата **`'a'`** при **`i = 0`**, **`'b'`** при **`i = 1`**, **`'c'`** при **`i = 2`** и т.н.

Така вече имаме генерирани всички 5-буквени комбинации и можем да продължим със следващата част от задачата.

***Внимание***: тъй като сме подбрали **`pattern`**, съобразен с азбучната подредба на буквите и циклите се въртят по подходящ начин, алгоритъмът ще генерира думите в азбучен ред и няма нужда от допълнително сортиране преди извеждане.
 
#### Премахването на повтарящи се букви

След като имаме вече готовия низ, трябва да премахнем всички повтарящи се символи. Ще направим тази операция, като **добавяме буквите от ляво надясно в нов низ и всеки път преди да добавим буква ще проверяваме дали вече я има** - ако я има ще я пропускаме, а ако я няма ще я добавяме. За начало ще добавим първата буква към началния стринг.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-05.png)

След това ще направим същото и с останалите 4, проверявайки всеки път дали ги има със следното условие и метода **`.IndexOf(…)`**. Това може да стане с цикъл по **`fullWord`** (оставяме това на читателя за упражнение), а може да стане и по мързеливия начин с copy-paste.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-06.png)

Методът **`.IndexOf(…)`** връща **индекса на конкретния елемент, ако бъде намерен или **`-1`**, ако елементът не бъде намерен**. Следователно всеки път, когато получим **`-1`**, ще означава, че все още нямаме тази буква в новия низ с уникални букви и можем да я добавим, а ако получим стойност различна от **`-1`**, ще означава, че вече имаме буквата и няма да я добавяме.

#### Пресмятане на теглото

Пресмятането на теглото е просто **обхождане на уникалната дума** (**`word`**), получена в миналата стъпка, като за всяка буква трябва да вземем теглото ѝ и да я умножим по позицията. За всяка буква в обхождането трябва да пресметнем с каква стойност ще умножим позицията ѝ, например чрез използването на **`switch`** конструкция.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-07.png)

След като имаме стойността на дадената буква, следва да я **умножим по позицията ѝ**. Тъй като индексите в стринга се различават с 1 от реалните позиции, т.е. индекс 0 е позиция 1, индекс 1 е позиция 2 и т.н., ще добавим 1 към индексите.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-08.png)

Всички получени междинни резултати трябва да бъдат добавени към **обща сума за всяка една буква от 5-буквената комбинация**.

#### Оформяне на изхода

Дали дадена дума трябва да се принтира, се определя по нейната тежест. Трябва ни условие, което да определи дали **текущата тежест е в интервала** [**начало … край**], подаден ни на входа в началото на програмата. Ако това е така, принтираме **пълната** дума (**`fullWord`**).

**Внимавайте** да не принтирате думата от уникални букви. Тя ни бе необходима само за пресмятане на тежестта!

Думите са **разделени с интервал** и ще ги натрупваме в междинна променлива **`result`**, която е дефинирана като празен низ в началото.

![](/assets/old-images/chapter-9-images/03.Five-special-letters-09.png)

#### Финални щрихи

Условието е изпълнено **с изключение случаите, в които нямаме нито една дума в подадения интервал**. За да разберем дали сме намерили такава дума, можем просто да проверим дали низът **`result`** има началната си стойност (а именно празен низ), ако е така - отпечатваме **`No`**, иначе печатаме целия низ без последния интервал (използвайки метода **`.Trim()`**).

![](/assets/old-images/chapter-9-images/03.Five-special-letters-10.png)

### Тестване в Judge системата

Тествайте решението си тук: [https://judge.softuni.bg/Contests/Practice/Index/518#2](https://judge.softuni.bg/Contests/Practice/Index/518#2).