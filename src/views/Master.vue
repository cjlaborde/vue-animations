<template>
  <div>
    <div id="container">
      <img class="paws first" src="../assets/paws.png" alt="fox-paws" />
      <img class="paws second" src="../assets/paws.png" alt="fox-paws" />
      <img class="paws third" src="../assets/paws.png" alt="fox-paws" />
      <img class="paws fourth" src="../assets/paws.png" alt="fox-paws" />

      <img id="fox" src="../assets/fox.png" alt="fox-logo" />
    </div>
    <button @click="play">Play</button>
  </div>
</template>

<script>
import gsap from 'gsap'
let masterTL = gsap.timeline()

export default {
  methods: {
    play() {
      masterTL.add(this.pawsTL())
      masterTL.add(this.foxTL())
      masterTL.play()
    },
    pawsTL() {
      let tl = gsap.timeline()
      tl.to('.first', {
        opacity: 4,
        scale: 1,
        duration: 0.5,
        ease: 'bounce.out'
      })
      tl.to(
        '.second',
        { opacity: 1, scale: 1, duration: 0.5, ease: 'bounce.out' },
        '<.3'
      )
      tl.to(
        '.third',
        { opacity: 1, scale: 1, duration: 0.5, ease: 'bounce.out' },
        '<.3'
      )
      tl.to(
        '.fourth',
        { opacity: 1, scale: 1, duration: 0.5, ease: 'bounce.out' },
        '<.3'
      )
      return tl
    },
    foxTL() {
      // 1) creating new timeline
      let tl = gsap.timeline()
      // 2) targeting the fox id
      tl.to('#fox', {
        // fading opacity to 1 and removing a blur
        opacity: 1,
        filter: 'blur(0)',
        // scaling the animation
        scale: 1,
        // animation duration
        duration: 0.4,
        ease: 'slow'
      })
      // return timeline so master timeline can use it.
      return tl
    }
  }
}
</script>

<style scoped>
#container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-top: 5em;
}

#fox {
  height: 8em;
  width: 8em;
  opacity: 0;
  filter: blur(2px);
}

.paws {
  transform: scale(0);
  width: 2.5em;
  height: 2.5em;
  margin-top: 50px;
  margin-right: 0.8em;
  opacity: 0;
}

button {
  margin-top: 5em;
}
</style>
