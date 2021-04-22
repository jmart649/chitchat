<template>
    <div class="fixed bottom-0 left-0 right-0 flex focus-within:ring-4 focus-within:ring-purple-800">
        <input v-model="newMessage" type="text" class="flex-grow text-xl font-thin focus:outline-none" @change="send" />
        <button class="bg-purple-800 px-8 focus:outline-none" @click="send" ><mdi:send-circle/></button>
    </div>
</template>

<script setup>
    import { ref, defineEmit } from 'vue'
    import { database } from '~/helpers/useFirebase'

    const { sendMessage } = database()

    const newMessage = ref(null)

    const emit = defineEmit(['added'])

    const send = () => {
    if (newMessage.value?.length > 0) {
        sendMessage(newMessage.value)
        newMessage.value = null
        emit('added')
    }
}
</script>