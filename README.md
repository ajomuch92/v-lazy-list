# v-lazy-list
A simple project to load a list lazily, ideally for large lists that need to be paginated

See an example [here](https://github.com/ajomuch92/v-lazy-list-example).

### Install  

NPM:  
```bash
npm i --save v-lazy-list
```

### Usage instructions  

Install the component globally

```javascript
import VLazyList from 'v-lazy-list';

Vue.use(VLazyList);
```

And use it inside your components

## Attributes

| Prop      | Type | Required |  Default  | Description |
|-----------|-----------|--------|----------|---------|
| items      |     Array   |    yes  |    []    |  A list with all the items to render into the list |
| loading      |     Boolean   |    no  |    false    |  A value to render the animated spinner icon |

## Event
| Name      | Description |
|-----------| -----------|
| on-load-more | Event triggered when the bottom is reached |


### Example

```html
<template>
  <v-lazy-list :items="items" :loading="loading" @on-load-more="loadRandomNumbers">
    <template #item="{value}">
      <p>This is the item => {{value.item}} and this is the index => {{value.index}}</p>
    </template>
  </v-lazy-list>
</template>
```

```javascript
export default {
  name: 'Example',
  data: () => ({
    items: [],
    loading: false,
  }),
  created() {
    this.loadRandomNumbers();
  },
  methods: {
    loadRandomNumbers() {
      this.loading = true;
      setTimeout(() => {
        for(let i = 0; i < 100; i+=1) {
          this.items.push(this.generateRandomNumber(1, 100))
        }
        this.loading = false;
      }, this.generateRandomNumber(800, 1000))
    },
    generateRandomNumber(begin, end) {
      return Math.floor(Math.random() * end) + begin;
    }
  }
}
```

**Note:** you can use the slot icon to pass a custom icon, but you have to animate it

