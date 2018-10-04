<template>
  <div class="admin">
    <div class="admin__list">
      <list></list>
    </div>
    <div class="admin__editor">
      <editor></editor>
    </div>
    <div class="admin__top-menu">
      <a href="http://blog.seekhow.cn" target="__blank"><i class="fa fa-home admin__top-menu__icon" aria-hidden="true"></i></a>
      <i class="fa fa-power-off" aria-hidden="true" @click="logout"></i>
    </div>
  </div>
</template>

<script>
import Editor from './Editor.vue';
import List from './List.vue';
import {
  mapMutations,
} from 'vuex';

export default {
  name: 'admin',
  components: {
    Editor,
    List,
  },
  methods: {
    ...mapMutations({
      deleteToken: 'DELETE_TOKEN',
    }),
    logout() {
      this.$confirm('此操作将退出系统, 是否继续?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning',
      }).then(() => {
        this.deleteToken();
        this.$router.push('/admin/login');
      }).catch();
    }
  }
};
</script>

<style lang="stylus" scoped>
@import '../assets/stylus/_settings.styl'
.admin
  &__list
    position fixed
    left 0
    top 0
    bottom 0
    width 500px
    overflow-y auto
    overflow-x hidden
  &__editor
    margin-left 500px
  &__top-menu
    position absolute
    top 22px
    right 30px
    font-size 28px
    cursor pointer
    color $blue
    &__icon
      margin 0px 20px
      color $blue
</style>
