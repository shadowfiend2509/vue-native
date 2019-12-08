<template>
  <scroll-view>
    <button @press="openDraw" title='Open Drawer' />
    <button @press="goToDetail" title='goToDetail'/>
    <view class='cards'>
      <view v-for='doto in dotoList' :key='doto._id'>
        <touchable-opacity :on-press="() => imageClick('parameter')">
          <image :source='{url: doto.vertical}' :style='{ width: 50, height: 50, marginLeft: 2, marginTop: 2 }' />
        </touchable-opacity>
      </view>
    </view>
  </scroll-view>
</template>

<script>
// import { axios } from '../apis';

export default {
  data () {
    return {
      dotoList: []
    }
  },
  props: [ 'navigation' ],
  methods: {
    imageClick (id) {
      console.log('masuk click', id)
    },
    goToDetail () {
      this.navigation.navigate('Details')
    },
    openDraw () {
      this.navigation.openDrawer()
    },
    async fetchDoto () {
      try {
        const response = await fetch('http://serverdoto.dreamcarofficial.com/hero')
        const { heroes } = await response.json();
        this.dotoList = heroes
      } catch(err) { console.log(err) }
    }
  },
  created() {
    this.fetchDoto()
  }
}
</script>

<style>
.cards {
  flex-direction: row;
  justify-content: center;
  align-items: center;
  padding: 7;
  flex-wrap: wrap
}
</style>