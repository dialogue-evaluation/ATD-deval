

# RuATD (Russian Artificial Text Detection)

[English](https://github.com/dialogue-evaluation/RuATD/blob/main/en_README.md)



## Мотивация

Современные модели генерации текстов показывают впечатляющие результаты: они могут сочинить стихотворение,  изменить стиль текстов и даже написать осмысленное эссе на свободную тематику. Однако такие модели могут быть использованы в злонамеренных целях, например, для генерации фейковых новостей, отзывов на продукты и политического контента. Так, возникает новая задача: научиться отличать тексты, написанные человеком, от текстов, сгенерированных нейросетевыми языковыми моделями. 

## Полезные ссылки

- Бинарная постановка: [kaggle](https://www.kaggle.com/c/ruatd-2022-bi/)
- Мультиклассовая постановка: [kaggle](https://www.kaggle.com/c/ruatd-2022-multi-task/)
- Группа в телеграм: [tlg](https://t.me/ruatd)

## Постановка задачи

Соревнование RuATD (Russian Artificial Text Detection) посвящено задаче автоматического распознавания сгенерированных текстов и предлагает участникам рассмотреть две постановки:

1. Определить, был ли текст сгенерирован автоматически или написан человеком;
2. Определить, какая именно модель была использована для генерации данного текста.

С формальной точки зрения, первая задача является задачей бинарной классификации, а вторая – мультиклассовой классификации. Обучающие и тестовые данные размечены автоматически. Тексты, написанные человеком, собраны из открытых источников. Различные нейросетевые языковые модели  – машинного перевода, парафразирования, суммаризации, упрощения и безусловной генерации текстов – использованы для генерации текстов. 

## Разметка и фрагмент данных

Схема бинарной разметки содержит следующие обозначения:

- H – текст написан человеком
- M – текст сгенерирован автоматически

Схема мультиклассовой разметки содержит следующие обозначения:

- OPUS-MT – текст сгенерирован моделью машинного перевода OPUS
- ruGPT3-Large – текст сгенерирован моделью ruGPT3-Large
- и так далее

Файлы [sample_submit_binary](https://github.com/dialogue-evaluation/RuATD/blob/main/sample_submit_binary.csv) и [sample_submit_multiple](https://github.com/dialogue-evaluation/RuATD/blob/main/sample_submit_multiple.csv) представляют формат данных для отправки на платформу соревнования. 

Пример обучающих данных представлен в таблице ниже. 

| H | M-MT (FR→RU) |
| --- | --- |
| Эх, у меня может быть и нет денег, но у меня всё ещё есть гордость. | Может, у меня нет денег, но у меня всегда есть гордость. |
| Меня покусали комары. | Меня похитили муски. |
| Я не могу чувствовать себя в гостинице как дома. | Я не могу чувствовать себя дома в отеле. |
| Эта книга показалась мне интересной. | Я нашёл эту интересную книгу. |
| Я был полон решимости помочь ему, даже рискуя собственной жизнью. | Я был готов помочь ему в опасности своей жизни. |
| Моя квартира находится меньше чем в пяти минутах пешком от станции. | Моя квартира находится на расстоянии менее пяти минут от станции. |

## Оценка решений

Для оценки решений в соревновании будет использована стандартная метрика оценки качества классификации — доля правильных ответов модели (accuracy).

## Базовые решения

Организаторы предоставят два базовых решения задачи:

- **tf-idf** + логистическая регрессия
- дообучение модели ruBERT

Код базовых решений будет доступен в репозитории соревнования. 

## Правила участия

# Регламент RuATD

1. Соревнование RuATD проводится на двух независимых платформах Kaggle:  бинарная классификация ([kaggle](https://www.kaggle.com/c/ruatd-2022-bi)) и мультиклассовая классификация ([kaggle](https://www.kaggle.com/c/ruatd-2022-multi-task/overview)).
2. Участникам разрешается использовать любые технологии и дополнительные данные, кроме **поиска в интернете** и **непосредственной разметки тестовых данных**. 
3. Тестовые файлы содержат одновременно и публичные, и приватные данные. В ходе тестирования будет открыт публичный лидерборд, по завершению тестирования – приватный лидерборд. 
4. Тестирование будет завершено 25 февраля 2022, 9 утра (Московское время). 
5. Для подсчета итогового результата на приватном лидерборде участник может выбрать три своих лучших решения. Если участник ничего не отметил автоматически выбираются три лучших сабмита по метрикам на публичном лидерборде.
6. Итоговые места присваиваются по результатам на приватном лидерборде (решения не прошедшие проверку в распределении мест не участвуют). 
7. С 25 февраля по 28 февраля будет проходить дополнительная стадия кросс-проверки полученных решений.
8. Участники получат ссылку на опросник,  в котором надо будет заполнить следующие поля: 
    1.  ответить на несколько вопросов об отправленном решении (для статьи организаторов на Диалог)
    2.  предоставить ссылку на решение в открытом доступе 
    3. или приложить код поданного решения. 
9. Полученные ссылки на решения организаторы распространят между участниками и попросят провести проверку. Мы попросим проверить следующие критерии: 
    1.  использует ли **решение поиск в интернете или нет**
    2.  использует ли **решение ручную разметку тестовых данных**
10. Организаторы обязаются так же участвовать в проверке решений и гарантируют, что каждое решение будет проверено. 
12. Решения, использующие поиск в интернете, будут дисквалифицированы и сняты с общих лидербордов.
13. Все участники соревнования будут приглашены к подаче статей в сборник Диалога (вне зависимости от того, было ли дисквалифицировано решение).
14. Статьи, посвященные дисквалицифированым решениям, получат дополнительную пометку, как проходящие вне общего конкурса.

## Ориентировочные сроки проведения соревнования

- Конец декабря 2021 - начало января 2022 – публикация обучающих данных
- 17 января 2022 – открытие платформ тестирования
- 25 февраля 2022, 9 утра (Мск) – закрытие тестирования
- 1-2 марта 2022 - официальное подведение итогов
- 15 марта 2022 – завершаем прием статей

## Организационный комитет

Екатерина Артемова (НИУ ВШЭ, Huawei Noah’s Ark Lab)

Анастасия  Валеева (МФТИ)

Константин Николаев (НИУ ВШЭ)

Владислав Михайлов (SberDevices)

Марат Саидов (НИУ ВШЭ)

Иван Смуров (ABBYY, МФТИ)

Елена Тутубалина (Sber)

Алена Феногенова (SberDevices)

Даниил Чернявский (Skolkovo Institute of Science and Technology)

Татьяна Шаврина (AIRI, SberDevices)

Татьяна Шамардина (ABBYY)
