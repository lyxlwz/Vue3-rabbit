<template>
  <div style="height: 2000px"></div>
  <!-- ð¯ç®æ åç´ éæ·»å æ¨¡æ¿ ref  -->
  <div ref="target">
    <h1>ð¯ææ¯ç®æ åç´ ð¯</h1>
  </div>
  <div style="height: 2000px"></div>
</template>

<script lang='ts'>
import { ref } from 'vue'
import { useIntersectionObserver } from '@vueuse/core'


/**
 * ðæ ¸å¿åè¯è§£éï¼
 *  useIntersectionObserver   æ£æ¥åç´ æ¯å¦è¿å¥å¯è§åºå½æ°
 *  target                    ç®æ åç´ ï¼ð¯ééåæ¨¡æ¿ ref ä½¿ç¨
 *  isIntersecting            æ¯å¦è¿å¥å¯è§åº(å¸å°å¼)
 *  stop                      ç¨äºåæ­¢æ£æµçå½æ°
 */

export default {
  name: 'index',
  components: {},
  mixins: [],

  props: {},
  setup(props, context) {
    // åå¤ç®æ åç´ (DOMèç¹æç»ä»¶ï¼ééåæ¨¡æ¿ ref ä½¿ç¨)
    const target = ref(null)

    const { stop } = useIntersectionObserver(target, ([{ isIntersecting }]) => {
      console.log('æ£æµåç´ å¯è§æ§', isIntersecting);
      // éæ±ï¼å¦æç®æ åç´ è¿å¥å¯è§åºï¼å°±åéè¯·æ±ï¼å¹¶åæ­¢æ£æµ
      if (isIntersecting) {
        // å½ç®æ åç´ è¿å¥å¯è§åºåæ¶ï¼æåéè¯·æ±
        console.log('è¿å¥å¯è§åºï¼éè¦åéè¯·æ±');
        // è¯·æ±å·²åéï¼ä¸»å¨åæ­¢æ£æ¥
        stop();
      }
    })

    return { target }
  },
}

</script>
<style lang='less' scoped>

</style>