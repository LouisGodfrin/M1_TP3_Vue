<template>
    <baseHeader />
    <BaseLayout />
    <ButtonLayout />
    <baseFooter />
</template>
  

<script>

import baseHeader from '../components/baseHeader.vue';
import baseFooter from '../components/baseFooter.vue';
import BaseLayout from '../components/BaseLayout.vue';
import ButtonLayout from '../components/ButtonLayout.vue'

export default {
    name : 'HomePage',
    components:
    {
        baseHeader,
        BaseLayout,
        baseFooter,
        ButtonLayout,
    }
}
</script>

<style>

</style>