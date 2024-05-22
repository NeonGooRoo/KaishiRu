# Kaishi 1.5k

Данная страница переведена машинно и пока что почти не проходила модерацию.

Добро пожаловать в публичный репозиторий **Kaishi 1.5k**, колоды карточек Anki, созданного для ознакомления начинающих с базовой японской лексикой. Kaishi 1.5k обладает высокой модульностью, и эта страница посвящена объяснению различных опций, которые вы можете использовать для изменения колоды по своему усмотрению. Вот как выглядит лицевая сторона колоды:

![image](https://github.com/NeonGooRoo/KaishiRu/assets/123720895/afa84330-1b74-4bc5-b0e8-a204450504e3)



Как видите, здесь представлены как слово, так и предложения, но слово выделено в предложении, что позволяет сразу изолировать важную информацию. Как только слово хорошо усвоено, повторение проходит быстрее, так как слово появляется первым. Вот оборотная сторона стандартной карточки:

![image](https://github.com/NeonGooRoo/KaishiRu/assets/123720895/8d7b5533-d5ed-4cfd-8372-c2b06730ffa5)


В отличие от большинства колод, здесь фуригана дает чтение слова, а значение находится прямо под ним. Вам доступны аудиозаписи для слова и предложения. Если хотите, можете также добавить акцентирование высоты тона, см. ниже. Если есть заметки, относящиеся к конкретной карточке, они отображаются внизу.

## Где получить колоду?

Вы можете получить колоду на [странице релизов](https://github.com/NeonGooRoo/KaishiRu/releases) этого GitHub или на [AnkiWeb](https://ankiweb.net/shared/info/1196762551), если колода не находится на проверке. **Колода поддерживается на Anki 2.1.50+**.

## Какие опции доступны для Колоды?

Существует множество опций для изменения ваших карточек. Чтобы изменить их, выберите колоду Kaishi, нажмите `Browse`, выберите любую карточку из колоды и нажмите `Cards...` в правом верхнем углу.

### Акцентирование высоты тона

Самая важная опция - это включение акцентирования высоты тона на ваших карточках. В настоящее время вопрос о том, следует ли изучать акцентирование высоты тона или нет, вызывает довольно горячие споры в сообществе. Мы решили занять среднюю позицию: данные об акцентировании высоты тона присутствуют, вы решаете, использовать их или нет. Если решите не использовать их, всегда можно включить позже. Включение акцентирования высоты тона просто. Вот настройки карточки в разделе `Back Template` для колоды (нажмите на маленькую точку над строкой `Search`).

```CSS
<div lang="ja">
{{furigana:Word Furigana}}

<!-- Этот блок включает акцентирование высоты тона.

{{#Pitch Accent}}
	<br><div style='font-size: 24px'>{{Pitch Accent}}</div>
{{/Pitch Accent}}

-->

<div style='font-size: 25px; padding-bottom:20px'>{{Word Meaning}}</div>
<div style='font-size: 25px;'>{{furigana:Sentence Furigana}}</div>
<div style='font-size: 25px; padding-bottom:10px'>{{Sentence Meaning}}</div>

{{Word Audio}}
{{Sentence Audio}}
<br>
{{Picture}}

{{#Notes}}
	<br>
	<div style="font-size: 20px; padding-top:12px">Note: {{Notes}}</div>
{{/Notes}}

<!-- Этот блок включает заметки об акцентировании высоты тона.

{{#Pitch Accent Notes}}
<div style="font-size: 20px; width: fit-content; max-width:40vw; margin: auto">
	<details><summary>Pitch Accent Notes</summary>
		<br>{{Pitch Accent Notes}}
	</details>
</div>
{{/Pitch Accent Notes}}

-->

</div>
Чтобы включить акцентирование высоты тона, просто удалите все части <!-- и -->, представляющие комментарии, вот так:

CSS
Copy code
<div lang="ja">
{{furigana:Word Furigana}}

{{#Pitch Accent}}
	<br><div style='font-size: 24px'>{{Pitch Accent}}</div>
{{/Pitch Accent}}

<div style='font-size: 25px; padding-bottom:20px'>{{Word Meaning}}</div>
<div style='font-size: 25px;'>{{furigana:Sentence Furigana}}</div>
<div style='font-size: 25px; padding-bottom:10px'>{{Sentence Meaning}}</div>

{{Word Audio}}
{{Sentence Audio}}
<br>
{{Picture}}

{{#Notes}}
	<br>
	<div style="font-size: 20px; padding-top:12px">Note: {{Notes}}</div>
{{/Notes}}

{{#Pitch Accent Notes}}
<div style="font-size: 20px; width: fit-content; max-width:40vw; margin: auto">
	<details><summary>Pitch Accent Notes</summary>
		<br>{{Pitch Accent Notes}}
	</details>
</div>
{{/Pitch Accent Notes}}

</div>

### Minor options

There are a couple of minor options you can modify.

#### Furigana
If you would like to take out furigana, simply take out the `furigana:` parts of the back template.

#### Other card options

You could entirely change the type of cards you want to see. Here is the `Front Template` of Kaishi 1.5k:

```CSS
<div lang="ja">
{{Word}}
<div style='font-size: 20px;'>{{Sentence}}</div>
</div>
```

Как видите, у нас есть только слово и предложение. Если вы хотите карточки *с предложением*, просто уберите часть `{{Word}}`, или вставьте `Sentence` вместо нее и уберите остальное. Если вы хотите карточки *со словом*, просто уберите `<div style='font-size: 20px;'>{{Sentence}}</div>`. Если же вы хотите карточки *с аудио*, уберите все и добавьте `{{Word Audio}}`, `{{Sentence Audio}}` или оба, если хотите оба варианта.

#### Изменение шрифтов, размера шрифта или других параметров стиля

Вот шаблон `Styling` для Kaishi 1.5k:


```CSS
.card {
 font-family: "ヒラギノ角ゴ Pro W3", "Hiragino Kaku Gothic Pro", "Noto Sans JP", Osaka, "メイリオ", Meiryo, "ＭＳ Ｐゴシック", "MS PGothic", "MS UI Gothic", sans-serif;
 font-size: 44px;
 text-align: center;
}

img {
max-width: 300px;
max-height: 250px;
}

.mobile img {
max-width: 50vw;
}

/* This part defines the bold color. */
b{color: #5586cd}
```
Вы можете найти различные параметры стилей [здесь](https://docs.ankiweb.net/templates/styling.html). Как видите, Kaishi 1.5k использует очень мало опций непосредственно на вкладке стилей. Вы можете изменить параметр `font-family`, чтобы получить разные шрифты, `font-size` для изменения размера шрифта и `text-align` для изменения выравнивания текста, например, если вы хотите, чтобы текст был выровнен по левому краю. По умолчанию Kaishi 1.5k выделяет **жирные** слова. Опция для изменения этого параметра — `b{color: }`, как показано выше. Просто вставьте hex-код или название цвета, например `red`, чтобы получить этот цвет. Если вы не хотите использовать цвет, просто уберите всю часть `b{color: }`.

## Как импортировать Kaishi 1.5k поверх другой колоды

Если вы уже начали использовать Core2k или Tango N4-N5 (или другую подобную колоду) и хотите переключиться на Kaishi 1.5k, вы можете следовать этим шагам, написанным [Kuuube](https://github.com/Kuuuube).

1. Импортируйте Kaishi как обычно с файлом .apkg.
2. Перейдите в `File > Export...` и экспортируйте колоду Kaishi, используя `Notes in Plain Text (.txt)`. Оставьте все остальные настройки по умолчанию.
3. Удалите колоду Kaishi.
4. Выберите колоду, на которую вы хотите импортировать Kaishi, выберите `Browse`, кликните любую карточку, нажмите `ctrl + a` и выберите `Notes > Change Note Type...` в верхнем левом меню.
5. Измените тип заметки на `Kaishi 1.5k`. Убедитесь, что в столбце `New` в поле `Word` отображается поле, которое ваша колода использует для слова.
    Если вы не собираетесь удалять какие-либо карточки из текущей колоды, которых нет в Kaishi, убедитесь, что ваши другие поля также выровнены по правильным местам. В противном случае, вы можете использовать настройки по умолчанию и нажать `Save`.
6. Импортируйте файл Kaishi .txt, экспортированный на шаге 2.
7. При импорте убедитесь, что тип заметки установлен на `Kaishi 1.5k`, а колода установлена на ту колоду, на которую вы хотите импортировать. 
    Если вы собираетесь удалять карточки, которых нет в Kaishi, добавьте тег `Kaishi` в опцию `Tag all notes`.
8. Нажмите `Import`.
9. Чтобы удалить карточки, которых нет в Kaishi, выберите свою колоду, нажмите `Browse`, выберите свою колоду в левом меню, добавьте ` -tag:Kaishi` в строку поиска, выберите любую карточку, нажмите `ctrl + a`, в верхнем левом меню перейдите в `Notes > Delete`.

**Если вы импортируете поверх Core 2.3k, пожалуйста, смотрите [здесь](https://github.com/Manhhao/anki.transfer-review-history).**

## Происхождение колоды

Эта колода возникла из обсуждения между Tyogin и мной на [сервере TMW в Discord](https://learnjapanese.moe/join/). Мы оба сожалели о том, что популярные колоды для начинающих в то время имели раздражающие недостатки. Начинающие постоянно путались при использовании Core 2k и Tango из-за различных проблем. В Tango были некоторые редкие слова, такие как ナンプラー, что является тайским рыбным соусом, и многим людям не были интересны все базовые фразы и названия стран, занимающие большую часть колоды. Поля колоды были ужасно отформатированы, что делало невозможным использование колоды иначе, чем предполагалось изначально, а именно как карточки с предложениями. Core 2k, с другой стороны, была модульной, но имела множество ошибок в переводах, отсутствующие или нерелевантные картинки, а некоторые предложения были не очень полезными, иногда даже не отражали значение используемого слова.

Обе эти проблемы были достаточно раздражающими, что мы получали вопросы от начинающих каждые две недели. Tyogin предложил решить эту проблему самим, и была собрана небольшая команда для исправления этих проблем. Мы в основном взяли данные из Core2k, Core10k, Tango N4 и Tango N5. Затем мы объединили данные, отсортировали слова по частоте, используя различные частотные словари Yomichan/Yomitan, и выбрали около 1500 слов. Затем мы исправили переводы для каждого слова, выбрали лучшее предложение для каждого слова и исправили предложение, если это было необходимо. Нам пришлось исправить примерно 120 предложений из выбранных 1500. После этого мы сгенерировали аудио для слов, у которых не было правильного аудио, и команда из двух человек (Karifurai и cindsa) проверила данные о тоновом акценте, которые мы получили из [AJT Japanese](https://ankiweb.net/shared/info/1344485230), а также добавила заметки о тоновом акценте для слов, которым это было необходимо. Затем мы удалили тишину на карточках и нормализовали уровень звука между различными файлами. Помимо этого, мы также сгенерировали фуригану из AJT Japanese для слов и предложений. После этого мы разработали базовый CSS для карточек с целевыми подсказками, который используется в стандартной версии колоды. Наконец, несколько человек вычитали колоду, чтобы убедиться, что у нас как можно меньше ошибок.

Kaishi, написанное как 開始, означает "начало". Мы подумали, что это подходит, поэтому решили использовать это название. Надеемся, что эта колода станет прекрасным началом вашего пути в изучении японского языка.

## Перевод колоды

Если вы заинтересованы в переводе колоды на свой родной язык, пожалуйста, создайте проблему на [трекере GitHub](https://github.com/donkuri/Kaishi/issues).

## Благодарности

Эта колода была создана с помощью следующих людей:

[栗](https://github.com/donkuri/) - главный архитектор, все технические аспекты, переводы, вычитка

Tyogin - главный архитектор, переупорядочил первые 200 карточек, изменил предложения, вычитка

shoui - вычитка всей колоды, исправление переводов

Julian - помог добавлять заметки и проверял некоторые переводы предложений

karifurai - проверил тоновый акцент для первых 750 карточек и добавил заметки о тоновом акценте

cindsa - проверил тоновый акцент для последних 750 карточек и добавил заметки о тоновом акценте

[Kuuube](https://github.com/Kuuuube) - предложил использование FFmpeg, написал раздел о переносе карточек в Kaishi 1.5k

[stephenmk](https://github.com/stephenmk) - запустил инструмент Jmdict Furigana на Kaishi 1.5k для исправления фуриганы, см. версию v1.3.0

[Kaanium](https://github.com/kaanium) - помог создать скрипт для конвертации колоды в письменную версию

Эти инструменты были использованы при создании колоды:

[AJT Japanese](https://github.com/Ajatt-Tools/Japanese) - тоновый акцент, фуригана и часть аудио были сгенерированы с использованием этого дополнения

[FFmpeg](https://ffmpeg.org/) - использовался для удаления некоторых тихих частей в различных аудиофайлах

[Tenacity](https://tenacityaudio.org/) - использовался для редактирования звуковых обрезок в различных аудиофайлах

Мы также получили различные идеи от нескольких участников сервера TMW в Discord, включая название самой колоды.


Переводили:

NeonGooRoo - ручной перевод, проверка машинного перевода на правильность, организация и оформление.
