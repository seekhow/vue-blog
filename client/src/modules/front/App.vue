<template>
  <div id="app">
    <div class="wrap">
      <Top></Top>
      <transition name="fade" mode="out-in">
        <!-- keep-alive排除article -->
        <keep-alive exclude="article_component">
          <router-view>
          </router-view>
        </keep-alive>
      </transition>
    </div>
    <footer class="footer">
      <p>Powered by <a href="https://github.com/seekhow/vue-blog">seekhow</a> forked from <a href="https://github.com/BUPT-HJM/vue-blog">BUPT-HJM/vue-blog</a></p>
    </footer>
    <!-- 防止disqus导致首页报错 -->
    <div id="disqus_thread"></div>
  </div>
</template>

<script>
import Top from './components/common/Top.vue';

export default {
  name: 'app',
  components: {
    Top,
  },
};
</script>

<style lang="stylus">
  @import 'assets/stylus/main.styl'
  @import 'assets/stylus/markdown.styl'
  $footer-height = 60px
  #app
    width 100%
    height 100%

  .fade-enter-active, .fade-leave-active
    transition all .2s ease

  .fade-enter, .fade-leave-active
    opacity 0

  .wrap
    min-height 100%
    margin-bottom -($footer-height)
  .wrap:after
    content ""
    display block
    height $footer-height
  .footer
    height $footer-height
    text-align center
    color $grey
    text-align center
    line-height 20px
    a
      text-decoration none
      color $blue-link
      &:hover
        text-decoration underline
  @media screen and (max-width: 850px)
    .fade-enter
      transform translate(30px, 0px)

    .fade-leave-active
      transform translate(-30px, 0px)
</style>
<style lang="stylus" scoped>
  #app
    #disqus_thread
      display none
</style>
