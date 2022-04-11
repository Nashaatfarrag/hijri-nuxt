# hijri

## Build Setup

```bash

# Google Analytics

<!-- Global site tag (gtag.js) - Google Analytics -->
<script async src="https://www.googletagmanager.com/gtag/js?id=UA-208155997-26"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'UA-208155997-26');
  gtag('config', 'AW-955968979'); 
</script>

#Important: place this right above the closing </body> tag

<script>
function send_conversion(){
console.log('Conversion triggered');
// Event snippet for Hijre lead conversion page
  gtag('event', 'conversion', {'send_to': 'AW-955968979/468HCODz6pQDENPb68cD'});
}

var elements = document.getElementsByClassName("v-chip__content");

for (var i = 0; i < elements.length; i++) {
    elements[i].addEventListener('click',send_conversion, false);
}

</script>	



# install dependencies
$ npm install

# serve with hot reload at localhost:3000
$ npm run dev

# build for production and launch server
$ npm run build
$ npm run start

# generate static project
$ npm run generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
