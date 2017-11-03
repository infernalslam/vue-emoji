<template>
  <div class="hello">
    <div v-for="(item, index) in list">
      <h1 style="font-size: 90px;">{{ item }}</h1>
    </div>
    <h1 style="font-size: 90px;"> {{ x[0] }} </h1>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      list: ['😴😄😃⛔🎠🚓🚇'],
      x: ['😴']
    }
  },
  mounted () {
    this.list = this.changeEmoji(JSON.stringify(this.list))
    // console.log(this.list)
  },
  methods: {
    changeEmoji (str) {
      let split = str.split(/([\uD800-\uDBFF][\uDC00-\uDFFF])/)
      let arr = []
      for (var i = 0; i < split.length; i++) {
        let char = split[i]
        if (char !== '' && char !== '["' && char !== '"]') {
          arr.push(char)
        }
      }
      return arr
    }
  }
}
</script>

