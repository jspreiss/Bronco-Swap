<template>
  <transition name="modal-animation">
    <div v-show="modalActive" class="modal">
      <transition name="modal-animation-inner">
        <div v-show="modalActive" class="modal-inner">
          <i @click="close" class="far fa-times-circle"></i>
          <div class="modalInfo">
            <img :src="passProduct.image" alt="This should be a photo" />
            <h1 class="itemTitle">{{ passProduct.title }}</h1>
            <p class="itemDesc">{{ passProduct.description }}</p>
            <p class="itemPrice">${{ passProduct.price }}</p>
            <p class="userInfo">
              Posted by: {{ passProduct.displayName }} ({{ passProduct.email }})
            </p>

            <button @click="close" type="button">Close</button>
          </div>
        </div>
      </transition>
    </div>
  </transition>
</template>
  
  <script>
export default {
  props: ['modalActive', 'passProduct'],
  setup(props, { emit }) {
    const close = () => {
      emit('close')
    }

    return { close }
  }
}
</script>
  
  <style lang="scss" scoped>
.modal-animation-enter-active,
.modal-animation-leave-active {
  transition: opacity 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-enter-from,
.modal-animation-leave-to {
  opacity: 0;
}

.modal-animation-inner-enter-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02) 0.15s;
}

.modal-animation-inner-leave-active {
  transition: all 0.3s cubic-bezier(0.52, 0.02, 0.19, 1.02);
}

.modal-animation-inner-enter-from {
  opacity: 0;
  transform: scale(0.8);
}

.modal-animation-inner-leave-to {
  transform: scale(0.8);
}

.modal {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0;
  left: 0;
  background-color: rgba(255, 255, 255, 0.7);

  .modal-inner {
    position: relative;
    max-width: 640px;
    width: 80%;
    box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    background-color: #F8f4f9;
    padding: 64px 16px;

    i {
      position: absolute;
      top: 15px;
      right: 15px;
      font-size: 20px;
      cursor: pointer;

      &:hover {
        color: crimson;
      }
    }

    .modalInfo {
      text-align: center;
      justify-content: center;

      img {
        max-width: 350px;
        min-width: 250px;
        margin-bottom: 15px;
        border-radius: 10px;
      }

      .itemPrice {
        font-size: 20px;
        color: #A5CC6b;
      }
    }

    button {
      padding: 20px 30px;
      border: none;
      font-size: 16px;
      background-color: #862633;
      color: #F8f4f9;
      cursor: pointer;
    }
  }
}
</style>