<template>
  <div v-if="isShow" :class="notificationType === 'success' ? 'quick-toastify-successful-notification' : 'quick-toastify-warn-notification'">
    <div class="quick-toastify-alert-toast">
      <div class="quick-toastify-alert-container">
        <div class="quick-toastify-successfull-icon">
          <SuccessfulIcon v-if="notificationType === 'success'"/>
          <WarningIcon v-else />
        </div>
        <p>{{ message }}</p>
        <div class="quick-toastify-cross-icon" @click="close">
          <CrossIcon />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import CrossIcon from './CrossIcon.vue';
import SuccessfulIcon from './SuccessfulIcon.vue';
import WarningIcon from './WarningIcon.vue';

export default {
  name: 'QuickToastify',
  components: {
    CrossIcon,
    SuccessfulIcon,
    WarningIcon
  },
  props: {
    notificationType: {
      type: String,
      default: 'success'
    },
    message: {
      type: String,
      default: 'Successfully Toasted!🤩'
    },
    isShow: {
      type: Boolean,
      default: true,
      required: true,
    },
    close:{
      type: Function,
      default: () =>{},
      required: true
    }
  },
  watch:{
    isShow(newValue){
      if(newValue){
        setTimeout(() => {
          this.close();
        }, 3500);
      }
    }
  }
};
</script>

<style scoped>
/* -------Notification alert toast------------ */

.quick-toastify-successful-notification {
    display: flex;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast {
    position: fixed;
    top: 50px;
    right: 30px;
    z-index: 9999;
    -webkit-animation: quick-toastify-fadeinout 3s linear forwards;
    animation: quick-toastify-fadeinout 3s ease-in-out forwards;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container {
    background: #ffffff;
    border: 1px solid #039855;
    box-shadow: 0px 7px 30px rgba(16, 5, 46, 0.08);
    border-radius: 10px;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    padding: 15px;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-successfull-icon,
.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon {
    height: 26px;
    width: 26px;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container p {
    padding: 0 60px 0 13px;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon {
    background: #ffffff;
    border: 1px solid #e4e6eb;
    border-radius: 6px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon svg path {
    fill: #686f7f;
}

.quick-toastify-successful-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon:hover {
    background: #e4e6eb;
}

.quick-toastify-successful-notification.quick-toastify-hide {
    display: none;
}

/* -------Warn notification alert toast------------ */

.quick-toastify-warn-notification {
    display: flex;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast {
    position: fixed;
    top: 120px;
    right: 30px;
    z-index: 9999;
    -webkit-animation: quick-toastify-fadeinout 3s linear forwards;
    animation: quick-toastify-fadeinout 3s ease-in-out forwards;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container {
    background: #ffffff;
    border: 1px solid #ec0707;
    box-shadow: 0px 7px 30px rgba(16, 5, 46, 0.08);
    border-radius: 10px;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    padding: 15px;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-successfull-icon,
.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon {
    height: 26px;
    width: 26px;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container p {
    padding: 0 60px 0 13px;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon {
    background: #ffffff;
    border: 1px solid #e4e6eb;
    border-radius: 6px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon svg path {
    fill: #686f7f;
}

.quick-toastify-warn-notification .quick-toastify-alert-toast .quick-toastify-alert-container .quick-toastify-cross-icon:hover {
    background: #e4e6eb;
}

@-webkit-keyframes quick-toastify-fadeinout {
    0% {
        opacity: 0;
        top: 80px;
    }
    20%, 80% {
        opacity: 1;
        top: 50px;
    }
    100% {
        opacity: 0;
        top: 20px;
    }
}

@keyframes quick-toastify-fadeinout {
    0% {
        opacity: 0;
        top: 80px;
    }
    20%, 80% {
        opacity: 1;
        top: 50px;
    }
    100% {
        opacity: 0;
        top: 20px;
    }
}
</style>
