<template>
    <div class="fixed top-0 left-0 right-0 bg-red-700 text-black py-6 z-10">
        <div class="container mx-auto flex justify-between items-center">
            <div class="brand flex space-x-2 text-3xl">
                <mdi:message-processing-outline />
                <h1 class="text-3xl font-thin">Chit<span class="font-bold">Chat</span></h1>
            </div>
            <div class="menu">
                <div v-if="!isAuthenticated">
                    <button
                    class="bg-green-700 text-white py-2 px-4 rounded-full hover:bg-green-900 focus:outline-none focus:ring-4 focus:ring-green-500"
                    @click="googlePopup">
                    Login
                    </button>
                </div>
                <div v-else class="flex items-center space-x-8">
                    <p>Welcome, {{ user?.displayName }}</p>
                    <button
                    class="bg-red-700 text-white py-2 px-4 rounded-full hover:bg-red-900 focus:outline-none focus:ring-4 focus:ring-red-500"
                    @click="signOut">
                    Logout
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
    import { authentication } from '~/helpers/useFirebase'
    const { isAuthenticated, user, googlePopup, signOut } = authentication()
</script>