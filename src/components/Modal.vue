<script setup lang="ts">
defineProps({
    show: Boolean,
    url: String
});
</script>

<template>
    <Transition name="modal">
        <div v-if="show" class="modal-mask">
            <div class="modal-container">
<button class="modal-default-button" @click="$emit('close')"><svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5">
  <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
</svg></button>
                <div class="modal-body">                        
                    
<slot name="body">
                        <img v-bind:src="url">
                    </slot>
                </div>

                <div class="modal-footer">
                    <slot name="footer">

                    </slot>
                </div>
            </div>
        </div>
    </Transition>
</template> 
  
<style scoped>
.modal-mask{
    @apply fixed z-50 top-0 left-0 w-full h-full flex justify-center items-center bg-gray-950/75 duration-200 ease-in-out
}

.modal-container{
@apply relative w-auto h-2/3 flex justify-center items-center bg-white p-4 rounded-lg drop-shadow-2xl duration-300 ease-in-out
}
.modal-body img{
@apply w-auto h-[inherit]
}

.modal-default-button{
    @apply absolute right-5 top-5 w-10 h-10
}

.modal-default-button svg{
    @apply stroke-white drop-shadow-lg
}

.modal-header h3 {
    margin-top: 0;
    color: #42b983;
}

.modal-body {
@apply w-full h-full flex justify-center items-center
}

.modal-default-button {
    float: right;
}

.modal-enter-from {
    opacity: 0;
}

.modal-leave-to {
    opacity: 0;
}

.modal-enter-from .modal-container,
.modal-leave-to .modal-container {
    -webkit-transform: scale(1.05);
    transform: scale(1.05);
}
</style>
