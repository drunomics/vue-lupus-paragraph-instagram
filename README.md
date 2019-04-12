# vue-lupus-paragraph-instagram
Vue instagram paragraph component.



## Install

via npm:
`npm install https://github.com/drunomics/vue-lupus-paragraph-instagram.git`


import it:

```
import PgInstagram from 'vue-lupus-paragraph-instagram';

Vue.component('pg-instagram', PgInstagram);
```


## Properties
You can pass the following props:

- `src` ( string )
  The instagram image url.


## Slots
You can use the following slots

- `title` ( default )
  A title.


## Example
```
<pg-instagram src="#the-instagram-post-link">
  <h3 slot="title">The title value</h3>
</pg-instagram>
```
