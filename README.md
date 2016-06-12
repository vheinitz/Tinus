# Tinus
 Что-то вроде социальной сети для пациентов
 
 
1 Общее Описание
================

Следующая проблема - в России/Украине очень мало гомеопатов и много негативной пропаганды против этого метода лечения. Цель сайта - облегчить людям принять решение для начала лечения гомеопатией (либо другими щадящими методами, напр. народной медициной.) Сайт позволяет непренуждённо ознамомитъся с процессом лечения и выбрать врача.

Начало лечения гомеопатией состоит в подробном описании болезни. При очном обращении к врачу-комеопату это описание болезн записывает сам врач при расспросе. Этот первый диалог врача с пациентом очень важен для успешного лечения и длится он в среднем 2 часа.

Идея, создать портал или что-то вроде социальной сети для заочного лечения. Каждый нуждающийся сможет описать свою болезнь по грамотно составленной анкете, и какой-либо гомеопат, консилиум гомеопатов или более сведующий пользователь сможет дать какие-то советы. Сайт должны мониторить грамотные люди. Совет может дать каждый, но у пользователей должен быть виден статус врач/не врач. Пациент решает сам верить не верить. Пациент сможет дать отчёт о проделанной терапии.

При заочном лечении пациент как правило заполняет очень подробную анкету. Заполнение анкеты длится долго - несколько дней. Поэтому заполнение анкеты - одна из самых важных сторон портала. Пациент может прервать, продолжить, изменить заполнение не зависимо от времени - за несколько раз. Вопросы должны содержать инструкции к ответу, по возможности проверять правильность ответа, где возможно (напр возрост, рост, вес). После заполнения пациент указывает что всё готово. И внести дополнение он сможет только по вопросу врача. Все данные принадлежат пациенту. При желании пациент может скачать анкету с ответами в форматах для дальнейшей обраборки и удалить свой аккаунт.

С таким сайтом/порталом барьер для лечитения гомеопатией был бы намного ниже чем сейчас - когда начало состоит в поиске гомеопата, обговаривании условий, цены, итд. С подобным порталом каждый нуждающийся сможет не таропясь заполнить анкету. При заполнении анкеты пациент уже получает первые представления о работе гомеопатии (или определённой терапии) - что в последствии облегчает общение с врачем. Пациент может послать ссылку любому врачу его доверия, и тот сможет посмотреть/скачать анкету.


В перспективе, система сможет анализировать случаи, советы и отчеты и уже при заполнении анкеты сама дать первые рекоммендации с использованием т.н. "искуственного интелекта".
Т.к. у многих людей из России/Украины, особенно у матерей-домохозяек (которые в основном и занимаются лечением семьи) единственная связь с интернетом это соц-сети, то система должно работать с медленной связью, с телефонами и с доступом через приложения в ВК, ОК.

Проект Open-Source и строго не коммерческий.

2 Техническое описание
======================

2.1 Роли
--------

Пользователь

 +- Админ
 
 +- Врач
 
 +- Пациент
 

2.1.1 Админ:
------------

  -разворачивает систему
  
  -Конфигурирует систему для 1/много врачей
  
  -Удаляет пользователей
  

2.1.2 Врач
-----------

  -Заполняет профиль (Опционально)
  
  -создаёт анкеты
  
  -принимает/отвергает/удаляет пациента.
  

2.1.3 Пациент
-------------

  -Выбирает врача
  
  -заполняет анкету


2.3 Структура анкеты
---------------------

 -Название (строчка, появляющаяся в списке)
 
 -Описание (Несколько строчек техта)
 
 -ИД кем создана
 
 -ИД от которой анкеты унаследована
 
 -Видимость (Толко определённые пациент/все)
 
 -Дата последней модификации
 
 -лог модификаций (техт)
 
 -Инструкции по заполнению (html-техт)
 

2.4 Структура Вопроса
---------------------

  -ИД парент-вопроса
  
  -Уровень (для быстрого показа глав, если можно без, тоже хорошо)
  
  -Условие, при котором показать суб-вопросы
  
  -Короткий вопрос (строчка)
  
  -более длинная версия (несколько строчек)
  
  -Инструкции для ответа (html. напр: введите число, кликните на картинке место)
  
  -Помощ (разяснение, почему такой вопрос, ссылки, информация - html)
  
  -Тип ответа (тип значения + тип ввода)
  
  -Возможно ли добавить файл (bool)
  
  -Возможно ли текстовое дополнение к ответу

Объяснение к ИД парент-вопроса: Опроник можно сделать в виде дерева. Вопросы могут являться контейнером для под-вопросов. При этом на вопрос можно ответить или нет. Так-же под-вопросы могут быть показаны или нет в зависимости от ответа на парент-вопрос.

Напр: Вопрос как контейнер главы: "Личные данные". 

   Тут ответ не нужен, пользователь просто нажимает на ОК прочитав инструкции.

Напр: Вопрос как главный с подвопросами: "Болит ли голова?"

  Тут при "да" появляются подвопросы напр "где, когда" итп.

2.5 Структура Ответа
--------------------

  -ИД вопроса
  
  -ИД анкеты
  
  -ИД пациента
  
  -ИД интервью
  
  -Дата ответа
  
  -Версия анкеты
  
  -ответ (значение зависит от типа)
  
  -Текстовый ответ (если разрешено в вопросе)
  
  -Прикрепленные файлы, (если разрешено в вопросе)
  

2.6 Структура Интервью
----------------------

  -ИД анкеты
  
  -ИД пациента
  
  -ИД Врача
  
  -Дата начала заполнения
  
  -Видимость (всем, только определённым пользователям)
