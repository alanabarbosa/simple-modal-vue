<template>
    <div class="container">
      <button 
        @click="modal = !modal"
      >
        Clique aqui
      </button>
        <div class="modal"  @click="clickOutside">
        <transition name="modal">
          <div class="container_modal" v-show="modal">
            <h1>Hello World!</h1>
          </div>
        </transition>
        </div>
    </div>
</template>

<script>
export default {
  name: 'ModalComponent',
  data () {
    return {
      modal: false
    }
  },
  methods: {
    clickOutside({ currentTarget, target}) {
      if (currentTarget == target) this.modal = false
    }
  },
}
</script>
<style scoped>
.container {
  background: #5429CF;
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 100vh;
  align-items: center;
  padding-top: 50px;
}

.container button {
  display: block;
  padding: 15px 28px;
  cursor: pointer;
}
.modal {
  display: flex;
  width: 100vw;
  height: 100vh;
  justify-content: center;
  padding-top: 40px;
}

.container_modal {
  display: flex;
  position: relative;
  height: 150px;
  width: 350px;
  align-items: center;
  justify-content: center;
  background: rgba( 255, 255, 255, 0.3 );
  box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
  backdrop-filter: blur( 5.5px );
  -webkit-backdrop-filter: blur( 5.5px );
  border-radius: 10px;
  border: 1px solid rgba( 255, 255, 255, 0.18 );
  animation: slide .3s;
}

.container_modal span {
  position: absolute;
  right: 0;
  top: -10px;
  border-radius: 50%;
  width: 25px;
  height: 25px;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  background: rgba( 255, 255, 255, 0.3 );
  box-shadow: 0 8px 32px 0 rgba( 31, 38, 135, 0.37 );
  backdrop-filter: blur( 5.5px );
  -webkit-backdrop-filter: blur( 5.5px );
  border: 1px solid rgba( 255, 255, 255, 0.18 );
}

.modal-enter,
.modal-leave-to {
  opacity: 0;
}

.modal-enter-active,
.modal-leave-to {
  transition: opacity 0.3s;
}

.modal-enter-to .modal {
  animation: slide 0.3s;
}

.modal-leave-to .modal {
  animation: slide 0.3s reverse;
}

@keyframes slide {
  from {
    transform: translate3d(0, -40px, 0);
  }
  to {
    transform: translate3d(0, 0px, 0);
  }
}
</style>
