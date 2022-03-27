# [HTML] Form - dropdown

## select

- 사용자 입력이 아닌 여러 옵션 중에서 선택하는 태그

### select 예제 1

```html
<div>
    <ul type="none">
        <li>
            <label for="fruit">좋아하는 과일 선택</label>
            <select id="fruit" name="fruit">
                <option value="사과">사과</option>
                <option value="바나나">바나나</option>
                <option value="복숭아">복숭아</option>
                <option value="배">배</option>
            </select>
        </li>
    </ul>
</div>
```

![예제1](/assets/img/posts/html-006/ex01.jpg)

### select 예제 2

```html
<div>
    <ul type="none">
        <li>
            <label for="channel">좋아하는 채널 선택</label>
            <select id="channel" name="channel">
                <optgroup label="지상파">
                    <option value="mbc">mbc</option>
                    <option value="kbs">kbs</option>
                    <option value="sbs">sbs</option>
                </optgroup>
                <optgroup label="종합편성채널">
                    <option value="ytn">ytn</option>
                    <option value="jtbc">jtbc</option>
                </optgroup>
            </select>
        </li>
    </ul>
</div>
```

![예제2](/assets/img/posts/html-006/ex02.jpg)

## datalist
- select와 비슷하나 직접 입력도 가능한 태그

```html
<div>
    <ul type="none">
        <li>
            <label for="fruit">좋아하는 과일 선택</label>
            <input type="text" id="fruit" name="fruit" list="fruit-list">
            <datalist id="fruit-list">
                <option value="사과">사과</option>
                <option value="바나나">바나나</option>
                <option value="복숭아">복숭아</option>
                <option value="배">배</option>
            </datalist>
        </li>
    </ul>
</div>
```
![예제3](/assets/img/posts/html-006/ex03.jpg)
