<template>
    <baseHeader />
    <mainPage />
    <baseFooter />
</template>
  

<script>

import baseHeader from '../components/baseHeader.vue';
import mainPage from '../components/mainPage.vue';
import baseFooter from '../components/baseFooter.vue';
export default {
    name : 'HomePage',
    components:
    {
        baseHeader,
        mainPage,
        baseFooter,
    }
}
</script>

<style>

</style>