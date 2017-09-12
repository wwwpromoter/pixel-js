# pixel-js
Pixel pass through redirect using javascript

## Setup
Firstly you'll need [url-polfill.js](https://github.com/wwwpromoter/pixel-js/blob/master/js/url-polyfill.js). This is a small script that allows us to accurately get values from the url so we can use it in our code.

Make sure to include it in your html page.

In our example it was:
```html
<script src="js/url-polyfill.js"></script>
```

## Implementation
Next we need to get the value from the url.
In our exmaple we're getting the `subid` from the url. Make sure you import the `url-polyfill` before doing this step. We're checking if a subid is there, then sending the user to the success page along with the subid.

```html
<script>
  const url = new URL(document.URL)
  
  if (url.searchParams.has('subid')) {
    var subid = url.searchParams.get('subid')
    document.location.href = './success.html?subid=' + subid
  }
</script>
```

#### Success
On the success page we then repeat the similar process of getting the value from the url, then setting the result to an image.

Firstly create the `img` tag and give it an id so we can use it later.
```html
<img id="subid-img" />
```

Then get the `subid` from the url and set it to the src of the img. The id we set on the img before is used to access it in this step.
```html
<script>
  const url = new URL(document.URL)
  if (url.searchParams.has('subid')) {
    const subid = url.searchParams.get('subid')
    document.getElementById('subid-img').setAttribute('src',
      'https://creative.wwwpromoter.com/conversion?c=29621&a=4132&ch=' + subid)
  }
</script>
```
