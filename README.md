# vue-lupus-paragrpah-instagram
Vue instagram paragraph component.



## Install

via npm:
`npm install https://github.com/drunomics/vue-lupus-paragraph-instagram.git`


import it:

```
import { PgInstagram } from 'vue-lupus-paragraph-instagram';

Vue.component('pg-instagram', PgInstagram);
```

## Options
You can pass options via props:

```
<pg-instagram
  type="{{ type }}"
  data-instagram-url="/instagram/url"
>
```
- `data-instagram-url` ( string )
  The pin's url.