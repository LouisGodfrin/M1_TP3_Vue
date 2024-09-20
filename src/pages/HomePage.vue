<template>
    <baseHeader />
    <BaseLayout />
    <baseFooter />
</template>
  

<script>

import baseHeader from '../components/baseHeader.vue';
import baseFooter from '../components/baseFooter.vue';
import BaseLayout from '../components/BaseLayout.vue';
export default {
    name : 'HomePage',
    components:
    {
        baseHeader,
        BaseLayout,
        baseFooter,
    }
}
</script>

<style>

</style>