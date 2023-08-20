<script  setup>
    import { ref } from 'vue';
    import ChildComponent from './ChildComponent.vue';
    import MessageComponent from './MessageComponent.vue';
    let messageFromParent = ref('Message from parent component to child component.')
    let messageFromChild = ref('')
    const  handleEmittedMessage=(emitedCustomMessage)=> {
        messageFromChild.value = emitedCustomMessage;
    }
</script>

<template>
  
<section class="bg-white dark:bg-gray-900">
    <div class="py-8 px-4 mx-auto max-w-screen-xl text-center lg:py-16">
        
        <MessageComponent v-if="messageFromChild.length>0" :message="messageFromChild" title="Message From Child" classProps="text-green-800 border border-green-300 rounded-lg bg-green-50 dark:bg-gray-800 dark:text-green-400 dark:border-green-800"/>
        <ChildComponent :messageFromParent="messageFromParent" @messageEmitted="handleEmittedMessage"/>
    </div>
</section>

</template>

<style scoped>

</style>