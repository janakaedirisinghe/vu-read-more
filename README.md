
# vu-read-more

This is a component/plugin designed for implementing read more functionality that is both straightforward and customizable and is intended to enhance the user experience. ❤️

## Usage

```sh
npm i vureadmore
```
```js
import  VuReadMore  from  'vureadmore'

app.component('VuReadMore', VuReadMore);  //Global Registration

components:  {  
	VuReadMore,  
},  //Local Registration
```

## Features
* Add text break characters length.
* Custom read more button text.
* Custom show less button text.
* Custom readmore/showless button styles.
* Custom text styles.
* Add only read more feature without show less.
* Add redirect link with new tab or same tab.

## API

| Param        | Data Type | Default                                                         | Description                                                                                                                          |
|--------------|-----------|-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
| `text`        | String    | none                                                            | This is used to format the read-more/show-less paragaph text based on the `charLength`                                                    |
| `charLength`   | Number    | 50                                                              | This is used to limit the `text` to generate read-more/show-less `text`                                                                      |
| `readMoreText` | String    | read more                                                       | This is used to change the `read more` button text                                                                                      |
| `readLessText` | String    | show less                                                       | This is used to change the `show less` button text                                                                                      |
| `buttonStyle`  | Object    | { color:'blue', cursor:'pointer', text-decoration:'underline' } | This is used to customize the read-more/show-less button styles                                                                        |
| `textStyle`    | Object    | none                                                            | This is used to customize the `text` styles                                                                                                      |
| `readMoreOnly` | Boolean   | false                                                           | Control the show-less function. You can use only read-more option here.                                                                 |
| `redirect`     | Object    | { `link`: '#', `newTab`: true }                                     | You can pass a link to navigate the user when the read more button is clicked. You can control the opening positions using `newTab` key. |

## Example

```js
<template>
  <span>
    <vu-read-more 
      :text="str" 
      :charLength="maxCharLength"
      readMoreText="Custom Read More Text" 
      readLessText="Custom Show Less Text" 
      :textStyle="textStyle"
      :buttonStyle="buttonStyles"
      :redirect="redirectObj"
    />
  </span>
</template>

<script>
import  VuReadMore  from  'vureadmore'

export default {
  name: 'App',
  data() {
    return {
      str: 'Lorem  dolor sit amet consectetur, adipisicing elit!',
      buttonStyles: { color: 'red', cursor: 'pointer' },
      redirectObj: { link: 'https://www.google.com', newTab: true },
      textStyle: { color: 'red' },
      maxCharLength: 150
    }
  },
  components: {
	  VuReadMore
  }
}
</script>
```