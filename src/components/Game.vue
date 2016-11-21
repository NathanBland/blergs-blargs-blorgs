<template>
  <div class="game">
    <div class='status' v-if="isConnecting">
      contacting remote server...
    </div>
    <div v-if="!isConnected && !isConnecting" class="notification is-warning">
      no connection
    </div>
    <div class="offline" v-if="!isConnected && !isConnecting">
      <button @click="goToClassSelect" v-if="!gameStarted" class="button">Start Offline Game</button>
      <div v-if="isPickingClass" class='is--picking-class'>
        <button class="button">
          <h2 class="subtitle is-2">I am a BLeRG</h2>
          <p>Smarter</p>
        </button>
        <button class="button">
          <h2 class="subtitle is-2">I am a BLaRG</h2>
          <p>Stronger</p>
        </button>
        <button class="button">
          <h2 class="subtitle is-2">I am a BLoRG</h2>
          <p>Faster</p>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      resources: {},
      isConnected: false,
      isConnecting: true,
      isPickingClass: false,
      gameStarted: false,
      season: 'Summer',
      race: ''
    }
  },
  created () {
    console.log('game started')
    this.isConnected = this.pingServer()
    setTimeout(() => {
      this.isConnecting = false
    }, 1500)
  },
  methods: {
    pingServer () {
      return false
    },
    goToClassSelect () {
      this.gameStarted = true
      this.isPickingClass = true
    }
  }
}
</script>

<style scoped lang="sass">
.game
  display: flex
  flex-flow: column nowrap

.is--picking-class
  display: flex
  justify-content: space-around
  
.is--picking-class button
  flex: 0
  height: unset
  display: flex
  flex-flow: column nowrap
  justify-content: center
</style>
