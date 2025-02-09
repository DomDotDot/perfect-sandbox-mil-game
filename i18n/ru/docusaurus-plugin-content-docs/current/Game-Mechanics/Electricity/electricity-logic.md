---
title: Electricity Laws
sidebar_position: 1
---

# Логика Электричества

1. Электрическая система в игре моделируется с учетом основных принципов работы электричества, но с упрощениями для обеспечения игрового баланса и удобства.

    1. Принципы работы: 
     Электричество в игре базируется на следующих ключевых понятиях: напряжение, ток, мощность, сопротивление.

        1. Напряжение (Вольты - В):

            1. Определение: Электрическое напряжение – это разность потенциалов между двумя точками электрической цепи, создающая "давление" для движения электрического тока.

            2. Наличие в цепи: Напряжение присутствует в цепи даже если она разомкнута (ток не течет).

            3. Регулирование: Напряжение регулируется блоками `Трансформатор` (повышение и понижение).

            4. Влияние на ток: Чем выше напряжение, тем большую силу тока можно "протолкнуть" через цепь (при прочих равных условиях).

            5. Необходимость для работы: Наличие напряжения необходимо для работы электрической цепи. Без напряжения электричество не будет функционировать.

            :::tip

            Аналогия
            Напряжение можно сравнить с давлением воды в водопроводе.

            :::

        2. Ток (Амперы - А):

            1. Определение: Электрический ток – это направленное движение электрических зарядов (электронов) по проводнику.

            2. Возникновение: Ток возникает только в замкнутой электрической цепи при наличии напряжения.

            3. Сила тока– это количество электрического заряда, протекающего через поперечное сечение проводника в единицу времени.

            4. Влияние нагрузки: Сила тока в цепи увеличивается с увеличением количества подключенных и включенных электрических приборов (нагрузки).

            5. Расчет: Ток в цепи рассчитывается как разделение потенциальной Мощности на напряжение 

            :::info

            Формула Мощности:
            (Ток = потенциальная Мощность / Напряжение)

            :::


            :::tip

            Аналогия
            Ток можно сравнить с количеством воды, протекающей по трубе в единицу времени.

            :::

        3. Мощность (Ватты - Вт):

            1. Определение: Электрическая мощность – это количество энергии, потребляемой или производимой электрическим устройством в единицу времени.

            2. Расчет: Мощность рассчитывается как произведение напряжения на силу тока 

            :::info

            Формула Мощности:
            (Мощность = Напряжение * Ток)

            :::

            Типы мощности:

                1. Генерируемая мощность: Общая мощность, производимая источниками энергии (например, турбинами).

                2. Потенциальная мощность: Мощность, необходимая для питания всех подключенных приборов в цепи при их полной нагрузке. Это максимальная мощность, которую цепь может потребовать.

                3. Максимальная мощность кабеля: Максимальная мощность, которую может безопасно пропустить через себя электрический кабель. Превышение этого значения приводит к перегреву и повреждению кабеля.

        4. Сопротивление (Омы - Ом):

            1. Определение: Электрическое сопротивление – это свойство материала или элемента цепи препятствовать прохождению электрического тока.

            2. Искусственное сопротивление (Резисторы): Резисторы используются для искусственного ограничения силы тока в цепи, чтобы защитить чувствительные приборы от перегрузки.

            3. Автоматическое сопротивление (в приборах): Электрические приборы имеют собственное внутреннее сопротивление, которое автоматически учитывается в электрической цепи.

            4. Натуральное сопротивление (провода): Сопротивление проводов зависит от их физических характеристик.

                :::note
                Увеличение сопротивления:

                    Большая длина провода

                    Малая толщина провода

                :::

                :::note
                Уменьшение сопротивления:

                    Малая длина провода

                    Большая толщина провода
                :::

    2. Замкнутость цепи: Электрическая цепь функционирует только при условии ее замкнутости. То есть, должен быть непрерывный путь для тока от источника напряжения к потребителям и обратно.

    3. Проводка:

        "Бесшовная проводка": В игре реализована система "бесшовной проводки" для упрощения подключения на коротких расстояниях. В пределах 100 стадов, электрические приборы можно подключать друг к другу напрямую через логические электрические входы/выходы, без явных проводов. Это уменьшает визуальный шум и упрощает строительство.

        Провода для больших расстояний: Для передачи энергии на расстояния более 100 стадов, необходимо использовать специальные провода для фазы и ноля. Эти провода создаются из медных блоков и физически соединяют электрические устройства. Такое разделение проводки обеспечивает реалистичность в дальних передачах и предоставляет игроку контроль над распределением энергии на больших территориях.

    4. Замыкание цепи: Неправильное замыкание цепи, например, до понижающего трансформатора или в середине фазы, приведет к короткому замыканию и выходу из строя электрической системы в этом месте.

2. Электрические приборы и Мощность

    1. Электрические приборы: Это блоки, которые для своей работы требуют электрической энергии. К ним относятся двигатели, лампы, радары, оружие и другие функциональные устройства.

    2. Параметры мощности приборов: Каждый электрический прибор имеет три ключевых параметра мощности:

        1. Минимальная мощность: Минимальная мощность (в ваттах), необходимая для начала работы прибора. Если мощность, поступающая на прибор, ниже минимальной, он не будет работать.

        2. Критическая мощность: Мощность, при которой прибор начинает работать на пределе своих возможностей и постепенно разрушаться. Работа на критической мощности не рекомендуется для длительного использования.

        3. Максимальная мощность: Максимальная мощность, которую прибор может выдержать. Превышение максимальной мощности приведет к немедленному разрушению/короткому замыканию прибора и его невозможности дальнейшего использования.

    3. Потребление мощности: В нормальных условиях, электрический прибор потребляет ровно столько мощности, сколько ему необходимо для эффективной работы в текущий момент. Однако, если в электрической сети недостаточно энергии, мощность, поступающая на прибор, может уменьшиться, что повлияет на его производительность.

    4. Влияние напряжения на приборы: Приборы, рассчитанные на определенное напряжение, могут быть повреждены, если напряжение в сети не соответствует их требованиям. Трансформаторы необходимы для согласования напряжения между разными частями электрической сети и защиты приборов от перенапряжения или недостатка напряжения.

    5. Мощность и производительность: Мощность (и, соответственно, напряжение) влияют на скорость и эффективность работы электрических приборов.

    :::tip
    Пример (Электрический мотор):

        1. Стандартная работа (100% КПД): Мотор, рассчитанный на 200 Вольт, при питании напряжением 200 Вольт работает с КПД 1.0 (стандартная производительность).

        2. Минимальная мощность (КПД ≈ 0): При подаче напряжения ниже минимального значения, мотор может не вращаться или вращаться очень медленно и неэффективно (КПД приближается к нулю).

        3. Максимальная мощность (КПД 2.0, но разрушение): При кратковременном повышении напряжения до максимального значения, мотор может работать с повышенной производительностью (например, КПД 2.0), но это приведет к его перегреву и разрушению в скором времени.
    :::

3. Аккумуляторы и Защита цепи

    1. Аккумуляторы: Аккумуляторы предназначены для накопления электрической энергии. При необходимости, они могут отдать накопленную энергию очень быстро, обеспечивая кратковременный всплеск мощности.

    2. Риск перегрузки: Резкая отдача мощности аккумуляторами может перегрузить провода, особенно если они рассчитаны на меньшую максимальную мощность. Это может привести к взрыву проводов.

    3. Щитки: Для защиты электрической цепи от перегрузок и коротких замыканий используются щитки (блоки предохранителей). Щитки устанавливаются в ключевых точках цепи и разрывают цепь при превышении допустимой мощности, предотвращая повреждение кабелей и приборов.

4. Иерархия электрической цепи

    Для создания надежной и эффективной электрической сети в игре рекомендуется придерживаться следующей иерархии:

        1. Генератор энергии (Турбина, Солнечная панель и т.п.): Источник производства электроэнергии.

        2. Аккумуляторы (Опционально): Накопление избыточной энергии для последующего использования.

        3. Щитки (Предохранители): Защита от перегрузок и коротких замыканий на начальном этапе цепи.

        4. Повышающий трансформатор: Повышение напряжения для передачи энергии на большие расстояния с меньшими потерями.

        5. Понижающий трансформатор: Понижение напряжения до необходимого уровня для питания приборов.

        6. Щитки (Предохранители): Дополнительная защита на участке цепи перед потребителями.

        7. Электрические приборы (Двигатели, Освещение, Логика и т.п.): Потребители электроэнергии.


    :::tip
        Пример простой электрической цепи:

        Турбина -> Аккумулятор -> Щиток -> Повышающий трансформатор -> Провод дальнего действия -> Понижающий трансформатор -> Щиток -> Прожектор
    :::