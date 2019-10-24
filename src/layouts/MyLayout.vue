<template>
  <q-layout view="lHh Lpr lFf">
    <q-img src="statics/bg.jpg" class="fixed-center fit" style="z-index: -1" />

    <q-header elevated>
      <q-toolbar>
        <q-btn flat dense round @click="menuDrawer = !menuDrawer" icon="menu" />

        <q-toolbar-title class="text-center">ACGN</q-toolbar-title>

        <q-img src="statics/app-logo-128x128.png" style="max-width: 48px" />
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="menuDrawer"
      bordered
      show-if-above
      content-class="text-center"
      :width="140"
      no-swipe-open
      no-swipe-close
    >
      <q-list>
        <q-item clickable @click="directTo = 'hot'">
          <q-item-section>
            <q-item-label>热点</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'pcgame'">
          <q-item-section>
            <q-item-label>单机游戏</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'netgame'">
          <q-item-section>
            <q-item-label>网络游戏</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'mobilegame'">
          <q-item-section>
            <q-item-label>移动游戏</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'anime'">
          <q-item-section>
            <q-item-label>动画</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'comic'">
          <q-item-section>
            <q-item-label>漫画</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'noval'">
          <q-item-section>
            <q-item-label>轻小说</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'cosplay'">
          <q-item-section>
            <q-item-label>Cosplay</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'tv'">
          <q-item-section>
            <q-item-label>剧集</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'movie'">
          <q-item-section>
            <q-item-label>电影</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'wallpaper'">
          <q-item-section>
            <q-item-label>壁纸</q-item-label>
          </q-item-section>
        </q-item>

        <q-expansion-item
          expand-separator
          dense-toggle
          label="绅士"
          ref="subMenu"
        >
          <q-list>
            <q-item clickable @click="directTo = 'hgame'">
              <q-item-section>游戏</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hanime'">
              <q-item-section>动画</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hcomic'">
              <q-item-section>漫画</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'himage'">
              <q-item-section>套图</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hmovie'">
              <q-item-section>电影</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hvideo'">
              <q-item-section>视频</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hvr'">
              <q-item-section>VR</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hnoval'">
              <q-item-section>小说</q-item-section>
            </q-item>

            <q-item clickable @click="directTo = 'hbase'">
              <q-item-section>车库</q-item-section>
            </q-item>
          </q-list>
        </q-expansion-item>

        <q-item clickable @click="directTo = 'bbs'">
          <q-item-section>
            <q-item-label>境界</q-item-label>
          </q-item-section>
        </q-item>

        <q-item clickable @click="directTo = 'report'">
          <q-item-section>
            <q-item-label>反馈</q-item-label>
          </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <div
      class="fixed-center fit"
      style="padding-left: 20px; padding-right: 20px; padding-top: 20px"
    >
      <q-page-container>
        <router-view
          style="min-height: 0; margin-top: 10px; margin-bottom: 10px"
        />
      </q-page-container>
    </div>
  </q-layout>
</template>

<script>
export default {
  name: "MyLayout",

  data() {
    return {
      menuDrawer: false,
      directTo: ""
    };
  },

  methods: {
    menuAuto() {
      if (this.directTo != "") {
        this.menuDrawer = false;
        this.directTo = "";
        this.$refs.subMenu.hide();
      }
    }
  },

  created() {
    window.addEventListener("click", this.menuAuto);
  },

  destroyed() {
    window.removeEventListener("click", this.menuAuto);
  }
};
</script>
