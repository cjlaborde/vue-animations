<template>
  <div id="container">
    <!-- <div id="square"></div>
    <div id="circle"></div>
    <div id="triangle"></div>-->
    <img class="runner first" src="../assets/runner.png" alt="runner" />
    <img class="runner second" src="../assets/runner.png" alt="runner" />
    <img class="runner third" src="../assets/runner.png" alt="runner" />
  </div>
</template>

<script>
import gsap from 'gsap'

export default {
  mounted() {
    //timeline code
    // let tl = gsap.timeline()
    // repeat timeline twixe
    // let tl = gsap.timeline({ repeat: 2 })
    // loop infinite with -1
    // let tl = gsap.timeline({ repeat: -1 })
    // repeatDelay is wait before it starts again
    let tl = gsap.timeline({ repeat: -1, repeatDelay: 1 })
    tl.to('.first', { x: 700, duration: 2, ease: 'expo.out' })
    // tl.to('.second', { x: 700, duration: 2, ease: 'expo.out' }, 0.5)
    // substract .75 seconds from 6 seconds making animation 5.25 seconds
    // tl.to('.second', { x: 700, duration: 2, ease: 'expo.out' }, '-=.75')
    // < makes animation fires same time as the first
    tl.to('.second', { x: 700, duration: 2, ease: 'expo.out' }, '<.5')
    tl.to('.third', { x: 700, duration: 2, ease: 'expo.out' }, '<')
    // use tl.duration() to calculate duration
  }
}
</script>

<style scoped>
.runner {
  display: block;
  height: 5em;
  width: 5em;
  margin-top: 1.5em;
}
#square {
  height: 6.5em;
  width: 6.5em;
  border-radius: 1%;
  background-color: #42b983;
  margin-top: 1em;
}

#circle {
  height: 6.5em;
  width: 6.5em;
  border-radius: 50%;
  background-color: #2c3e50;
  margin-top: 1em;
}

#triangle {
  width: 0;
  height: 0;
  border-left: 4em solid transparent;
  border-right: 4em solid transparent;
  border-bottom: 6em solid #16c0b0;
  margin-top: 1em;
}
</style>
