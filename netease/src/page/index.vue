<template>
<div>
 <nHeader></nHeader>
 <nAside></nAside>
 <nArticle></nArticle>
 <nPlayer></nPlayer>
</div>
</template>
<script>
import nHeader from '../components/Header.vue'
import nAside  from '../components/Aside.vue'
import nArticle  from '../components/Article.vue'
import nPlayer from '../components/Player.vue'
export default{
  name: 'index_page',
  components:{
    nHeader,
    nAside,
    nArticle,
    nPlayer
  }
}
</script>

