<template>
<div>
 <nHeader></nHeader>
 <nAside></nAside>
 <nArticle></nArticle>
 <nPlayer></nPlayer>
</div>
</template>
<script>
import nHeader from '../components/nHeader.vue'
import nAside  from '../components/nAside.vue'
import nArticle  from '../components/nArticle.vue'
import nPlayer  from '../components/nPlayer.vue'
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

