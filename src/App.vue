  <template>
  <button @click="loading">123</button>
  <div>
    <router-link to="/">首页</router-link> |
    <router-link to="/about">关于</router-link>
  </div>
  <router-view></router-view>
</template>
<script setup>
import useFavicon from './utils/favicon'
let { favicon } = useFavicon()
function loading() {
  favicon.value = '/geek.png'
}
</script>