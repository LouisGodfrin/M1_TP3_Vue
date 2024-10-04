<template>
    <div class = "asynchrone">
        <async-component @click="denied"/>
    </div>
    <ButtonLayout />
</template>
  

<script>
import AsyncComponent from '../components/AsyncComponent.vue';
import ButtonLayout from '../components/ButtonLayout.vue'

export default 
{
    name : 'HomePage',
    components:
    {
        AsyncComponent,
        ButtonLayout,
    },

    data: () => ({
        clickCount: 0,
    }),
    methods:
    {
        denied()
        {
            return new Promise((resolve) => 
            {
                setTimeout(() => 
                {
                this.clickCount++;
                console.log(this.clickCount);
                resolve();
                }, 2 * 1000);
            });
        }
    }
}
</script>

<style>

</style>