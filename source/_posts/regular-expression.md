---
title: regular-expression
date: 2018-04-30 14:16:27
tags:
---

Today, I realize that the [regular expression] is so powerful. The following is a comparison.

I have demand that add a comma between digitals every three digits(the int part) in a number.
this is a solution here using a while Statements :
{% codeblock lang:js %}
  function addCommas(nu) {
    const numStr = num.toString().split('.');
    let intPart = numStr[0];
    const floatPart = numStr[1].length ? '.' + numStr[1] : '';
    while(intPart.length > 4 && reg.test(intPart)) {
      intPart = intPart.replace(reg, '$1' + ',' + '$1');
    }
    return intPart + floatPart;
  }
{% endcodeblock%}
And this is the second solution just with regular expression, the logic is more concise:
{% codeblock lang:js %}
  function addCommas(num, comma = ',') {
    const numStr = num.toString().split('.');
    intPart[0] = intPart[0].replace(/\B(?=(\d{3})+(?!\d))/g, comma);
    return numStr.join('.');
  }
{% endcodeblock %}
Before, I think there is a solution to solve your problem without regular expression, so I don't have to learn regular expression deeply. It's no doubt that you can deal with problems with multiple ways, but I should have forgot to find a more efficient way. Well, I determine to learn regular expression again, the follwing are my notes of the regular expression.

First there are special characters in regular expression:
1. \
A backslash that precedes a non-special character indicates that the next character is special and is not to be interpreted literally. For example, '\b'
2. ^
Matches beginning of input. If the multiline flag is set to true, also matches immediately before a line break character.
{% codeblock lang:js %}
  const str = 'abc';
  str.match(/^a/); // 'a' will be matched
{% endcodeblock %}
3. $ 
Matches end of input. If multiline flag is set to true, also matches immediately before aline break character.
{% codeblock lang:js %}
  const str = 'dfg'
  str.match(/g$/); 'g' will be matched
{% endcodeblock %}
4. *
Matches the preceding expression 0 or more times. Equivalent to {0,}.
{% codeblock lang:js %}
  const reg = /bo*/;
  'A ghost boooooed'.match(reg); // 'booooo' will be matched
  'A bird warbled'.match(reg); // 'b' will be matched
  'A goat grunted'.match(reg); // nothing will be matced
{% endcodeblock %}
5. '+'
Matches the preceding expression 1 or more times. Equivalent to {1,}.
{% codeblock lang:js %}
  const reg = /bo+/;
  'A ghost boooooed'.match(reg); // 'booooo' will be matched
  'A bird warbled'.match(reg); // nothing  will be matched
{% endcodeblock %}

To be continued.


