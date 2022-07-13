# vue-share-to-social

A simple dynamic table build with vue.js

### [npm](https://www.npmjs.com/package/vue-share-to-social)
### [github](https://github.com/JISSJOHNSON/vue-share-to-social)

## Installation

```
npm i --save vue-share-to-social
```

### Importing globally into app

```
import VueShareToSocial from 'vue-share-to-social';

Vue.use(VueShareToSocial);
```

### Importing into your component

```
import VueShareToSocial from 'vue-share-to-social';

components:{
  VueShareToSocial
}
```

### Usage

```
<template>
  <vue-share-to-social :items="tableHeading"></vue-share-to-social>
</template>

<script>
import VueShareToSocial from 'vue-share-to-social';
...
components:{
  ...,
  VueShareToSocial
},
data(){
  return{
      items: [
      // default items in module is listed as string you can remove these if not needed
      // if you want to modify any item, add those as object
        'mail',
        'linkedin',
        'twitter',
        'facebook',
        'whatsapp',
      // If you want to add new items just add as following
        {
          name: 'telegram',
          url: 'https://telegram.me/share/url?url=',
          icon: 'https://img.icons8.com/color/search/instagram',
        },
      ],
  }
}
...
</script>
```

#### Author

[Jiss Johnson](https://jissjohnson.info)
