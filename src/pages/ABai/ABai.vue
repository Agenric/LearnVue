<template>
  <div class="abai">
    <keep-alive>
      <component
        :is="currentTabComponent"
        class="content" />
    </keep-alive>
    <tab-bar
      :tabs="tabBarItems"
      class="tab-bar"
      @didSelectTab="didSelectTab" />
  </div>
</template>

<script>
import TabBar from '../../components/ABai/TabBar'
import Home from './Home'
import Profile from './Profile'

export default {
  components: {
    'tab-bar': TabBar,
    'home': Home,
    'profile': Profile
  },
  data () {
    return {
      currentTab: null,
      tabItems: ['home', 'profile'],
      tabBarItems: [
        {
          title: '首页',
          iconNormal: require('../../assets/ABai/tabbar/tabbar_index_normal.png'),
          iconHighlight: require('../../assets/ABai/tabbar/tabbar_index_highlight.png')
        },
        {
          title: '个人中心',
          iconNormal: require('../../assets/ABai/tabbar/tabbar_profile_normal.png'),
          iconHighlight: require('../../assets/ABai/tabbar/tabbar_profile_highlight.png')
        }
      ]
    }
  },
  computed: {
    currentTabComponent: function () {
      return this.currentTab
    }
  },
  methods: {
    didSelectTab: function (index) {
      this.currentTab = this.tabItems[index]
      console.log(index)
    }
  }
}
</script>

<style lang="less" scoped>
.abai {
  align-content: center;
  background-color: rgb(241, 240, 240);
  .content {
    width: inherit;
    padding-bottom: 64px;
  }
  .tab-bar {
    left: 0;
    position: fixed;
    bottom: 0;
    width: 100%;
    z-index: 100;
  }
}
</style>
