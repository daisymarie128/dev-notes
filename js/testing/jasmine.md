## Jasmine
Jasmine is a behavior-driven development framework for testing JavaScript code. It does not depend on any other JavaScript frameworks. It does not require a DOM.

example of how to write a test using jasmine.js

Write your test first for whatever component you need to make.<br>
For this example we just want a button that replaces text in another element.
```js
describe('text changer button', () => {
	it("should replace text with 'im the new text'", () => {
  browser.url('http://bs-local.com:8080/');

	const myButton = $('.o-btn--test')
  const text = browser.getText('.text-block');

  browser.click('.o-btn--test');

  expect(text).toBe('im the new text');
	})
});
```

Next try and write your code to pass this test.
HTML:
```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Testing</title>
</head>
<body>
  <div id="container">
			<button class="o-btn o-btn--test">Click me</button>
			<h3 class="text-block" >This text will change</h3>
  </div>
</body>
</html>
```

Javascript:
```Javascript
const button = document.getElementsByClassName('o-btn--test')[0];
const textBlock = document.getElementsByClassName('text-block')[0];

button.addEventListener('click', () => {
	textBlock.innerHTML = 'working';
});
```
