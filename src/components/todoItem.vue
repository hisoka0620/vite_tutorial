<template>
    <li :style="li">
      {{ title }}
      <button @click="$emit('remove')" :style="commonStyle">削除</button>
    </li>
</template>

<script>
export default {
  name: 'todoItem',
  props: ['title'],
  data(){
    return{
      li: {
        listStyle: 'none',
        marginBottom: '5px'
      },
      commonStyle: {
        color: 'white',
        backgroundColor: 'pink',
        border: '1px solid white',
        outline: 'none',
        padding: '6px 10px',
        cursor: 'pointer'
      },
    }
  }
}

</script>
