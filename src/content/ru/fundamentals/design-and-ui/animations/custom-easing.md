project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: Сойдите с наезженной дороги и создайте абсолютно нестандартную анимацию для своего проекта

{# wf_review_required #}
{# wf_updated_on: 2014-10-20 #}
{# wf_published_on: 2014-08-08 #}

# Изменение скорости при нестандартной анимации {: .page-title }

{% include "web/_shared/contributors/paullewis.html" %}
{% include "web/_shared/contributors/samthorogood.html" %}


Иногда не хочется использовать ключевые слова изменения скорости, имеющиеся в CSS, или же используется библиотека анимации на основе JavaScript. В обоих случаях, как правило, можно определить собственные кривые (или формулы), а это позволяет в значительной степени влиять на ощущение, которое будет создавать анимация в вашем проекте

## TL;DR {: .hide-from-toc }
- Нестандартное изменение скорости позволяет добиться большей индивидуальности проектов.
- 'Можно создавать кривые Безье третьего порядка, которые похожи на стандартные кривые анимации (замедления, ускорения и т. д.), но с другим акцентом.'
- 'Когда требуется в большей мере контролировать время и работу анимации (например, эластичные эффекты или отскоки), используйте JavaScript.'


Если анимация создается средствами CSS, то с помощью определения кривых Безье третьего порядка можно управлять ее привязкой ко времени. В действительности, ключевые слова `ease`, `ease-in`, `ease-out` и `linear` сопоставляются с заранее заданными кривыми Безье, о чем подробно говориться в статье [Определение переходов CSS](http://www.w3.org/TR/css3-transitions/).

В CSS эти кривые Безье принимают четыре значения, или две пары чисел, при этом каждая пара описывает координаты X и Y контрольных точек кривой Безье третьего порядка.  Начальная точка кривой Безье имеет координаты (0, 0), а конечная ― координаты (1, 1). Вам же необходимо указать значения X и Y двух оставшихся контрольных точек. Значения X для этих двух контрольных точек должны находиться в диапазоне от 0 до 1, а значение Y каждой контрольной точки может выходить за пределы диапазона [0, 1], хотя в спецификации и нет четкого указания насколько!

При изменении значений X и Y каждой контрольной точки образуется совершенно другая кривая и, соответственно, ваша анимация будет создавать совершенно иное ощущение. Например, если первая контрольная точка находится внизу справа, анимация будет медленной в начале. Если же она будет находиться вверху слева, начало будет быстрым. И наоборот, если вторая контрольная точка находится на сетке внизу справа, анимация будет быстрой в конце, а если вверху слева ― медленной.

Для сравнения, вот две кривые: стандартная кривая с ускорением и замедлением и нестандартная кривая:

<img src="imgs/ease-in-out-markers.png" style="display: inline; max-width: 300px" alt="Кривая анимации с ускорением и замедлением." />
<img src="imgs/custom.png" style="display: inline; max-width: 300px" alt="Нестандартная кривая анимации." />

<a href="https://googlesamples.github.io/web-fundamentals/samples/../fundamentals/design-and-ui/animations/box-move-custom-curve.html">См. описание анимации с нестандартным изменением скорости.</a>

Код CSS для нестандартной кривой:


    transition: transform 500ms cubic-bezier(0.465, 0.183, 0.153, 0.946);
    

Первые два числа – это координаты X и Y первой контрольной точки, вторые два числа – это координаты X и Y второй контрольной точки.

Делать нестандартные кривые очень интересно, кроме того, вы получаете значительную степень контроля над тем ощущением, которое вызывает анимация. Например, говоря о приведенной выше кривой, можно отметить, что она похожа на классическую кривую ускорения-замедления, когда анимация имеет медленную скорость в начале и в конце, однако отрезок времени с медленной скоростью в начале укорочен, а в конце – продлен.

Поэкспериментируйте с этим <a href="https://googlesamples.github.io/web-fundamentals/samples/../fundamentals/design-and-ui/animations/curve-playground.html">средством создания кривых анимации</a> и оцените, как используемая кривая влияет на ощущение, создаваемое анимацией.

## Использование JavaScript для большего контроля

Иногда нужен еще более высокий уровень контроля, чем тот, который обеспечивается кривой Безье третьего порядка. Скажем, вам может потребоваться реализовать эластичный отскок или остановить выполнение анимации. И того, и другого эффекта намного сложнее добиться с помощью CSS. В подобных случаях следует использовать библиотеки анимации JavaScript. Одной из лучших библиотек является [TweenMax от Greensock](https://github.com/greensock/GreenSock-JS/tree/master/src/minified) (или TweenLite, если вы не хотите ничего усложнять). Эта небольшая библиотека дает вам значительную степень контроля, кроме того это весьма тщательно подобранная база кодов.

<a href="https://googlesamples.github.io/web-fundamentals/samples/../fundamentals/design-and-ui/animations/box-move-elastic.html">См. анимацию с эластичным изменением скорости.</a>

Чтобы применить нечто наподобие TweenMax, включите в страницу следующий скрипт:


    <script src="http://cdnjs.cloudflare.com/ajax/libs/gsap/latest/TweenMax.min.js"></script>
    

После этого можно будет вызывать TweenMax для вашего элемента и указывать, какие свойства вам нужны, а также любое требуемое изменение скорости. Есть множество вариантов изменения скорости, в приведенном далее коде используется эластичное замедление:


    var box = document.getElementById('my-box');
    var animationDurationInSeconds = 1.5;
    
    TweenMax.to(box, animationDurationInSeconds, {
      x: '100%',
      ease: 'Elastic.easeOut'
    });
    

В [документации по TweenMax](http://greensock.com/docs/#/HTML5/GSAP/TweenMax/) описаны все имеющиеся варианты, поэтому рекомендуем ее почитать.


