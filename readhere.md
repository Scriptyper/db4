# Вопросы к 4 коллоку

1. **Как формулируется задача проектирования реляционной базы данных? Какие цели при этом преследуются?**

> Логическое проектирование реляционной БД сводится к созданию реляционной схемы БД, в которой будут определены базовые отношения их атрибуты и ограничения целостности, достаточно полно отражающие семантику предметной области.
> Цели:
> 1. Возможность хранения всех необходимых данных в БД.
> 2. Исключение избыточного дублирования данных.
> 3. Сведение числа хранимых в БД отношений к минимуму.
> 4. Нормализация отношений для упрощения решения проблем, связанных с вставкой, обновлением и удалением данных.

2. **Что такое универсальное отношение?**

> Универсальное отношение – это **отношение, в которое включаются все представляющие интерес атрибуты ПрО** и которое может таким образом содержать все данные, предполагающиеся к хранению в БД.

3. **Какие аномалии могут возникать при использовании «некачественных» отношений?**

> - **Аномалия вставки** - новый студент ещё не закончил ни один курс, поэтому *курс, семестр, оценка* - пустые поля
> - **Аномалия удаления** - студентка не закончила курс, её удалили из базы из-за несоответствия данных
> - **Аномалия обновления** - студентка, записанная несколько раз меняет тел номер комнаты, надо менять все записи этой студентки, если у неё есть соседка, а она об этом не сказала, то за комнатой будут числиться два номера

4. **Укажите условие первой нормальной формы отношений.**

> Отношение находится в первой нормальной форме (1НФ), **если каждый его элемент имеет и всегда будет иметь атомарное значение**.

5. **Что такое декомпозиция отношения? Для чего она используется?**

> Декомпозициия - **процесс разбиения отношения с целью уменьшения вероятности возникновения аномалий**.

6. **С помощью какой операции над отношениями осуществляется декомпозиция?**

> **С помощью проекции**.  
> Декомпозиция осуществляется с помощью функциональной зависимости между атрибутами в рассматриваемом отношении. 

7. **Каких правил следует придерживаться при выборе ФЗ для очередной декомпозиции?**

> - Простым правилом выбора ФЗ для декомпозиции может служить поиск цепочек ФЗ вида A -> B -> C с последующим использованием крайней правой зависимости. (B -> C)
> - Более общее правило выбора ФЗ для декомпозиции – всеми средствами следует избегать выбора ФЗ, зависимая часть которой сама, целиком или частично, является детерминантом другой ФЗ

8. **Какая операция является обратной декомпозиции?**

> **Операция соединения** - исходное отношение равно соединению его проекций, полученных в ходе декомпозиции

9. **Как в теории реляционных БД определяется функциональная зависимость (ФЗ)? Какое отображение стоит за этим понятием? Что является источником информации о ФЗ?**

> - Если даны два атрибута A и B, то говорят, что B функционально зависит от A, если для каждого значения A существует не более одного связанного с ним значения B. 
> - За этим понятием стоит функциональное отображение. 
> - Единственным источником информации о функциональной зависимости для схемы отношения является семантика его атрибутов. В этом смысле зависимости являются фактически высказываниями о закономерностях реального мира.

10. **Что такое детерминант атрибута?**

> Если A -> B и B не зависит функционально от любого подмножества A, то говорят, что A представляет собой детерминант B.

11. **Что такое возможный ключ отношения?**

> Возможный ключ – **подмножество атрибутов отношения, имеющие свойства: уникальность, несократимость.** Другими словами, несократимый суперключ.

12. **Определите условие нормальной формы Бойса-Кодда (НФБК).**

> Отношение находится в нормальной форме Бойса-Кодда, в том случае, **если каждый детерминант атрибутов отношения является возможным ключом отношения.**

13. **Приведите первоначальный алгоритм нормализации отношений до НФБК.**

> 1. Указываем соображения, послужившие основой выделений этих ФЗ.
> 2. Определяем детерминанты
> 3. Находим минимальный набор атрибутов. По нему находим возможный ключ
> 4. Если каждый детерминант в отношении является возможным ключом, то отношение находится в НФБК.

14. **Укажите желательные свойства декомпозиции. Дайте им определения.**

> Свойства декомпозиции:
> 1. **Соединение без потерь** - желательно т.к. позволяет восстановить любой кортеж исходного отношения
> 2. **Сохранение зависимостей** - желательно т.к. позволяет сохранить все ограничения, наложенные на исходное отношение

15. **В чем заключается метод синтеза? Приведите пример.**

> Метод синтеза - подход, при котором необходимо **все ФЗ с одинаковыми детерминантами выделить в группы и для каждой группы построить свое отношение, куда включить все атрибуты всех ФЗ этой группы.**

16. **Что такое избыточная ФЗ?**

> Избыточная ФЗ - **зависимость, не заключающая в себе такой информации, которая не могла бы быть получена на основе других зависимостей** из числа использованных при проектировании БД.

17. **Перечислите правила вывода ФЗ.**

> - А1 - **Рефлексивность** A,X -> X
> - А2 - **Пополнение** A -> B => A,Z -> B,Z и A,Z -> B
> - А3 - **Транзитивность** A -> B и B -> C => A -> C
> - П4 - **Объединение** A -> B и A -> C => A -> B,C
> - П5 - **Декомпозиция** A -> B,C => A -> B и A -> C
> - П6 - **Псевдотранзитивность** A -> B и B,Z -> C => A,Z -> C

18. **Какими свойствами обладают аксиомы Армстронга?**

> Аксиомы Армстронга обладают
> - **надежностью** (если зависимость X -> Y выведена из F с помощью этих аксиом, то она справедлива в любом отношении, в котором справедливы зависимости из F.),
> - **полнотой** (когда зависимость X -> Y не может быть выведена из F с помощью этих аксиом, она логически не следует из F.),
> - **непротиворечивостью** (аксиомы не позволяют вывести какие-либо дополнительные функциональные зависимости, которые не следовали бы из F.)

19. **Как определять избыточные ФЗ с использованием правил вывода ФЗ? Приведите пример.**

> ![image](https://github.com/user-attachments/assets/64f9ff1e-c32f-47ed-b6b7-e1ead4f03d95)

20. **Что такое минимальное покрытие ФЗ отношения?**

> Минимальное покрытие ФЗ отношения - это набор неизбыточных ФЗ, полученный путем удаления всех избыточных ФЗ из исходного набора с помощью 6 правил вывода.

21. **Как окончательно выглядит декомпозиционный алгоритм проектирования реляционных схем БД?**

> **1.** Построение универсального отношения. Оно пока является единственным в очереди еще не проверенных на НФБК отношений.  
> **2.** Определение всех ФЗ, существующих между атрибутами этого отношения.  
> **3.** Удаление всех избыточных ФЗ из исходного набора ФЗ с целью получения минимального покрытия.  
> **4.** Использование ФЗ из минимального покрытия для декомпозиции универсального отношения в набор НФБК-отношений.  
> **4.1.** Определение ФЗ минимального покрытия для очередного отношения.  
> **4.2.** Определение того, находится ли очередное отношение в НФБК. Если да, то проектирование для него завершается, если нет – это отношение декомпозируется на два новых, которые помещаются в очередь еще не проверенных на НФБК отношений.  
> **4.3.** Повторение шагов 4.1 и 4.2 для каждого очередного отношения. Проектирование завершается, когда очередь еще не проверенных на НФБК отношений опустеет, а, значит, все полученные отношения находятся в НФБК.  
> Если может быть построено более чем одно минимальное покрытие, осуществляется сравнение результатов, полученных на основе этих минимальных покрытий, с целью определения варианта, лучше других отвечающего требованиям ПрО.

22. **Какие проверки отношений следует провести на завершающей фазе проектирования?**

> **1.** Составляются списки ФЗ для каждого отношения. Эти списки ФЗ проверяются по двум направлениям:  
> **1.1.** Одна и та же ФЗ не должна появляться более чем в одном отношении.  
> **1.2.** Набор ФЗ, полученный в результате проектирования, должен в точности совпадать с набором, присутствующем в минимальном покрытии, полученном перед началом проектирования. В противном случае, необходимо показать возможность получения итогового набора ФЗ из минимального покрытия с помощью правил вывода и наоборот.  
> **2.** Осуществляется проверка на присутствие избыточных отношений. Если устанавливается избыточность отношения, его следует исключить из проектного набора. Отношение является избыточным, если:  
> **2.1.** все атрибуты этого отношения могут быть найдены в одном другом отношении проектного набора;  
> **2.2.** все атрибуты этого отношения могут быть найдены в отношении, которое может быть получено из других отношений проектного набора с помощью серии операций соединения над этими отношениями.  
> **3.** Отношения рассматриваются с практической точки зрения. Изучается характер использования отношений в конструируемой БД и определяется, будут ли они обеспечивать те типы запросов и операций обновления, которые предполагается выполнять.  
> Если хотя бы одна из этих проверок окажется недостоверной, следует проанализировать процесс проектирования для выявления ошибок и/или рассмотреть другие варианты проектирования

### **Вопросы и задания к параграфу 5.1**

23. **Каковы основные недостатки классической методики проектирования реляционных БД?**

> - нетрадиционный для людей способ восприятия и формализации ПрО;
> - практическая неприменимость для анализа сложных ПрО; 
> - неоднозначность решения проблемы проектирования, граничащая с прямым перебором многочисленных вариантов схемы в поисках наиболее подходящего. 

24. **Как выглядит основная схема любой семантической методики проектирования БД?**

> - проектирование семантической схемы ПрО с использованием той или иной модели; 
> - перевод схемы в реляционную модель с применением подходящего набора правил трансформации и получение множества предварительных отношений; 
> - проверка полученных отношений на удовлетворение требований нормальных форм, и дальнейшая нормализация методом декомпозиции.  
> Все семантические методики действуют по одной и той же схеме и отличаются лишь используемыми моделями и правилами трансляции схем.

25. **Укажите этапы расширенной семантической методики проектирования БД?**

> - функциональное моделирование бизнес-процессов предприятия, для информационного обеспечения которых создается БД;
> - семантическое моделирование данных в рамках той или иной семантической модели;
> - получение логической схемы БД в понятиях логической модели выбранной СУБД;
> - настройка БД на языке физической модели СУБД.

26. **Какие доводы можно привести в пользу необходимости внесения изменений синхронно в артефакты всех этапов проектирования, включая самые ранние?**

27. **Каковы цели этапа анализа потребностей задач ПрО? Каким образом они достигаются?**

> - Изучение области деятельности моделируемой организации.
> - Определение информационных потребностей организации; при этом единственное существенное ограничение, которое должно учитываться – адекватность процессам функционирования организации.
> - Обеспечение представления указанных потребностей с помощью техники формального моделирования.

28. **Для чего предназначены различные функциональные модели ПрО?**

29. **В каких понятиях описывается функционирование организации в деловой модели? Что стоит за этими понятиями?**

30. **Каковы основные принципы построения деловой модели?**

31. **Как в дальнейшем будет использоваться деловая модель ПрО на последующих этапах семантической методики?**

### **Вопросы и задания к параграфу 5.2**

32. **Какова главная стратегия процесса семантического моделирования с использованием деловой модели, как исходного артефакта, и ER-модели, как целевого формализма для представления семантической схемы БД?**

33. **Какие этапы выделяются в этом процессе? Какие задачи решаются в ходе этих этапов?**

34. **На какие вопросы необходимо дать ответ при определении множеств сущностей?**

35. **На какие вопросы необходимо дать ответ при определении множеств связей?**

36. **На какие вопросы необходимо дать ответ при определении ограничений целостности?**

37. **По каким правилам осуществляется интеграция подсхем в общую ER-схему ПрО?**

38. **Что представляет собой генерализация множеств связей?**

### **Вопросы и задания к параграфу 5.3**

39. **Какая задача решается на этапе логического проектирования данных?**

40. **Какие действия предусмотрены на этапе логического проектирования данных для реляционной модели? В каких случаях они выполняются?**

41. **Какие факторы в основном влияют на успех применения семантической методики?**

42. **Вспомните простейшие правила перехода от ER-схемы к реляционной схеме БД.**

43. **За счет чего повышается качество схемы при использовании усовершенствованных правила перехода от ER-схемы к реляционной схеме БД?**

44. **Какие решения предлагают усовершенствованные правила для множеств связей типа 1:1? Какими рассуждениями следует сопровождать применение этих правил?**

45. **Какие решения предлагают усовершенствованные правила для множеств связей типа 1:_M_? Какими рассуждениями следует сопровождать применение этих правил?**

46. **Как изменились решения в случае однозначных атрибутов множеств связей?**

47. **Какими методами могут быть представлены в реляционной модели специализации и категоризации?**

48. **Какие критерии могут направлять процесс выбора метода представления специализаций и категоризаций?**

49. **Какие факторы необходимо учесть при выборе метода?**

50. **Какой принцип используется для денормализации отношений на завершающем этапе логического проектирования?**

51. **Опишите типичные случаи денормализации.**

### **Вопросы и задания к параграфу 5.4**

52. **Какие действия осуществляются на этапе физического проектирования данных?**

53. **Какие виды сегментов предоставляет СУБД Oracle для хранения таблиц?**

54. **Каких правил следует придерживаться при построении индексов?**

55. **Какими параметрами команды CREATE TABLE определяются требования к дисковой памяти?**
