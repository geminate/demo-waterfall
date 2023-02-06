<template>
  <div id="app">
    <h2>1. 元素宽高均相同 & 列数固定</h2>
    <div class="container-1">
      <div v-for="(item,i) in list" :key="i"><img :src="item.url" alt=""/></div>
    </div>
    <hr>
    <h2>2. 元素宽高均相同 & 列数自适应</h2>
    <div class="container-2">
      <div v-for="(item,i) in list" :key="i" :style="{backgroundImage:'url(' + item.url + ')'}"></div>
      <i></i><i></i><i></i><i></i>
    </div>
    <hr>
    <h2>3. 元素仅宽相同 & 高度自适应 & 列数固定</h2>
    <div class="container-3">
      <div v-for="(item,i) in list" :key="i"><img :src="item.url" alt=""/></div>
    </div>
    <hr>
    <h2>4. 元素仅宽相同 & 高度自适应 & 列数自适应</h2>
    <div class="container-4">
      <div v-for="(item,i) in list" :key="i"><img :src="item.url" alt=""/></div>
    </div>
    <hr>
    <h2>5. 元素仅高相同 & 宽度自适应</h2>
    <div class="container-5">
      <div v-for="(item,i) in list" :key="i"><img :src="item.url" alt=""/></div>
    </div>
    <h2>6. 每行元素高相同 & 行高自适应 & 宽度自适应</h2>
    <div class="container-6">
      <div v-for="(item,i) in list" :key="i"
           :style="{flexGrow: item.width / item.height,flexBasis: item.width / item.height * 200 + 'px'}">
        <img :src="item.url" alt=""/>
        <i :style="{paddingBottom:item.height / item.width * 100 + '%'}"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      list: [
        {
          url: require('./assets/1.jpg'),
          width: 642,
          height: 903
        },
        {
          url: require('./assets/2.jpg'),
          width: 1354,
          height: 903
        },
        {
          url: require('./assets/3.jpg'),
          width: 364,
          height: 243
        },
        {
          url: require('./assets/4.jpg'),
          width: 363,
          height: 242
        },
        {
          url: require('./assets/5.jpg'),
          width: 363,
          height: 240
        },
        {
          url: require('./assets/6.jpg'),
          width: 851,
          height: 397
        },
        {
          url: require('./assets/7.jpg'),
          width: 294,
          height: 196
        },
        {
          url: require('./assets/8.jpg'),
          width: 291,
          height: 194
        },
        {
          url: require('./assets/9.jpg'),
          width: 1285,
          height: 903
        },
        {
          url: require('./assets/10.jpg'),
          width: 317,
          height: 211
        },
        {
          url: require('./assets/11.jpg'),
          width: 1350,
          height: 903
        },
        {
          url: require('./assets/12.jpg'),
          width: 329,
          height: 219
        },
        {
          url: require('./assets/13.jpg'),
          width: 330,
          height: 220
        },
        {
          url: require('./assets/14.jpg'),
          width: 602,
          height: 903
        },
        {
          url: require('./assets/15.jpg'),
          width: 602,
          height: 903
        }
      ]
    }
  }
}
</script>

<style lang="less">
h2 {
  text-align: center;
}

img {
  display: block;
}
</style>
<style lang="less">
.container-1 {
  width: 1000px;
  margin: 0 auto;
  overflow: hidden;
  border: 1px solid darkgray;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;

  div {
    width: 247px;
    height: 247px;
    margin-bottom: 4px;

    &:last-child:nth-child(4n - 1) {
      margin-right: 251px
    }

    &:last-child:nth-child(4n - 2) {
      margin-right: 502px;
    }
  }

  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
<style lang="less">
.container-2 {
  width: 100%;
  margin: 0 auto;
  overflow: hidden;
  border: 1px solid darkgray;
  display: flex;
  flex-wrap: wrap;

  div {
    flex: 1 0 250px;
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;
    margin: 2px;
    position: relative;
    overflow: hidden;

    &:after {
      padding-bottom: 150%;
      content: '';
      display: block;
    }
  }

  i {
    margin: 2px;
    flex: 1 0 250px;
    height: 0;
  }
}
</style>
<style lang="less">
.container-3 {
  width: 1000px;
  margin: 0 auto;
  column-count: 4;
  column-gap: 4px;
  overflow: hidden;
  border: 1px solid darkgray;

  div {
    break-inside: avoid;
    margin-bottom: 4px;

    img {
      object-fit: cover;
      width: 100%;
    }
  }
}
</style>
<style lang="less">
.container-4 {
  width: 100%;
  margin: 0 auto;
  column-count: 2;
  column-gap: 4px;
  overflow: hidden;
  border: 1px solid darkgray;

  div {
    break-inside: avoid;
    margin-bottom: 4px;

    img {
      object-fit: cover;
      width: 100%;
    }
  }
}

@media (min-width: 768px) {
  .container-4 {
    column-count: 3;
  }
}

@media (min-width: 992px) {
  .container-4 {
    column-count: 4;
  }
}

@media (min-width: 1200px) {
  .container-4 {
    column-count: 5;
  }
}
</style>
<style lang="less">
.container-5 {
  width: 100%;
  margin: 0 auto;
  border: 1px solid darkgray;
  display: flex;
  flex-wrap: wrap;

  &:after {
    content: '';
    display: block;
    flex-grow: 99999;
  }

  div {
    margin-right: 4px;
    margin-bottom: 4px;
    flex-grow: 1;

    img {
      object-fit: cover;
      height: 300px;
      width: 100%;
    }
  }
}
</style>
<style lang="less">
.container-6 {
  width: 100%;
  margin: 0 auto;
  border: 1px solid darkgray;
  display: flex;
  flex-wrap: wrap;

  &:after {
    content: '';
    flex-grow: 999999999;
  }

  div {
    flex: 1 0 200px;
    position: relative;
    overflow: hidden;
    background: red;
    margin: 2px;

    &:after {
      content: '';
      display: block;
      flex-grow: 99999;
    }

    i {
      display: block;
    }

    img {
      position: absolute;
      top: 0;
      width: 100%;
    }
  }
}
</style>
