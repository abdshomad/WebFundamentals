project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description: 使用正确的输入类型来简化信息输入操作。 用户喜欢在输入电话号码时网站会自动显示数字键盘，或随着输入信息而自动跳换字段。 寻找机会消除表单中的多余点击。

{# wf_review_required #}
{# wf_updated_on: 2014-10-20 #}
{# wf_published_on: 2000-01-01 #}

# 选择最佳输入类型 {: .page-title }

{% include "_shared/contributors/TODO.html" %}


使用正确的输入类型来简化信息输入操作。 用户喜欢在输入电话号码时网站会自动显示数字键盘，或随着输入信息而自动跳换字段。 寻找机会消除表单中的多余点击。


## TL;DR {: .hide-from-toc }
- 选择最适合数据的输入类型，以简化输入操作。
- 通过<code>datalist</code> 元素在用户输入时提供建议值。


### HTML5 输入类型

HTML5 引入了大量新的输入类型。 这些新输入类型可以提示
浏览器，屏幕键盘应显示什么类型的
键盘布局。  用户无需切换键盘，就能更轻松地输入
所需的信息，并且只看到该输入类型
的相应按键。

<table class="mdl-data-table mdl-js-data-table">
  <thead>
    <tr>
      <th data-th="Input type">输入 <code>type</code></th>
      <th data-th="Typical keyboard">典型键盘</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td data-th="Input type">
        <code>url</code><br> 用于输入 URL。 其开头必须是有效的 URI 格式，
例如 <code>http://</code>、<code>ftp://</code> 或 <code>mailto:</code>。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/url-ios.png" srcset="imgs/url-ios.png 1x, imgs/url-ios-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>tel</code><br>用于输入电话号码。 它<b>不</b>
执行特定的验证语法，因此，如果要确保
特定的格式，可以使用模式属性。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/tel-android.png" srcset="imgs/tel-android.png 1x, imgs/tel-android-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>email</code><br>用于输入电子邮件地址，并提示
键盘上应默认显示 @。 如果需要用户提供多个电子邮件地址，
则可以添加 multiple 属性。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/email-android.png" srcset="imgs/email-android.png 1x, imgs/email-android-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>search</code><br>一个文本输入字段，其样式与
平台的搜索字段一致。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/plain-ios.png" srcset="imgs/plain-ios.png 1x, imgs/plain-ios-2x.png 2x" class="keybimg">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>number</code><br>用于数字输入，可以是任意合理的
整数或浮点值。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/number-android.png" srcset="imgs/number-android.png 1x, imgs/number-android-2x.png 2x" class="keybimg">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>range</code><br>用于数字输入，但与 number 输入
类型不同，其值没那么重要。 它作为滑块控件
显示给用户。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/range-ios.png">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>datetime-local</code><br>用于输入日期和时间值，
提供的时区为本地时区。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/datetime-local-ios.png" srcset="imgs/datetime-local-ios.png 1x, imgs/datetime-local-ios-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>date</code><br>用于只输入日期，不提供
时区。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/date-android.png" srcset="imgs/date-android.png 1x, imgs/date-android-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>time</code><br>用于只输入时间，不提供
时区。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/time-ios.png" srcset="imgs/time-ios.png 1x, imgs/time-ios-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>week</code><br>用于只输入星期，不提供
时区。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/week-android.png" srcset="imgs/week-android.png 1x, imgs/week-android-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>month</code><br>用于只输入月份，不提供
时区。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/month-ios.png" srcset="imgs/month-ios.png 1x, imgs/month-ios-2x.png 2x">
      </td>
    </tr>
    <tr>
      <td data-th="Input type">
        <code>color</code><br>用于选取颜色。
      </td>
      <td data-th="Typical keyboard">
        <img src="imgs/color-android.png" srcset="imgs/color-android.png 1x, imgs/color-android-2x.png 2x">
      </td>
    </tr>
  </tbody>
</table>

### 使用 datalist 在输入时提供建议值

`datalist` 元素不是输入类型，而是与一个表单字段关联的
建议输入值的列表。 它允许浏览器在用户输入时
建议自动完成选项。 `datalist` 元素与 select 元素不同，它无需用户浏览长列表来
找出所需的值，也不限制用户只能选择
这些选项，此元素在用户输入时提供提示。

<pre class="prettyprint">
{% includecode content_path="web..//fundamentals/design-and-ui/input/forms/_code/order.html" region_tag="datalist" %}
</pre>

<!-- TODO: Verify note type! -->
Note: <code>datalist</code> 值是提供的建议值，并不意味着用户 只能选择所提供的建议值。

