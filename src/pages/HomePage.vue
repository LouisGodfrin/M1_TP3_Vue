<template>
    <div>
      <AsyncComponent @click="denied" />
    </div>
  
    <div>
      <ButtonLayout :isDisabled="isDisabled" @click="handleClick">
        {{ isDisabled ? 'Disabled' : 'Click Me' }}
      </ButtonLayout>
  
      <ButtonLayout :style="{ width: buttonWidth + 'px', height: buttonHeight + 'px' }"
      :class="{ bigger: isBigger, max: isMax }" @click="BiggerWeight" :isDisabled ="isMax"> 
        Bigger
      </ButtonLayout>
    </div>
  
    <div>
      <ButtonLayout :buttonWidth="200" :buttonHeight="40" color="primary">
          Great
      </ButtonLayout>
    
      <ButtonLayout :buttonWidth="200" :buttonHeight="40" color="warn">
          Warning
      </ButtonLayout>
    
      <ButtonLayout :buttonWidth="200" :buttonHeight="40" color="danger">
          Danger
      </ButtonLayout>
    </div>

</template>
  
  <script>
  import AsyncComponent from '../components/AsyncComponent.vue';
  import ButtonLayout from '../components/ButtonLayout.vue';
  
  export default 
  {
    name: 'HomePage',
    components: 
    {
      AsyncComponent,
      ButtonLayout,
    },
    data() 
    {
      return {
        isDisabled: false,
        isBigger: false,
        isMax: false,
        buttonWidth: 200,
        buttonHeight: 40,
        //click: 0,
      };
    },
    methods: 
    {
        handleClick() 
        {
            this.isDisabled = true;
        },

        BiggerWeight() 
        {
            if (!this.isMax) 
            {
                this.buttonWidth += 20;
                this.buttonHeight += 20;
                if (this.buttonWidth >= 300 && this.buttonHeight >= 300) 
                {
                this.isMax = true;
                }
            }
        },

        denied() 
        {
            return new Promise((resolve) => 
            {
            setTimeout(() => 
            {
                // this.clickCount++;
                // console.log(this.clickCount);
                resolve();
            }, 2* 2000);
            });
        },
    },
  };
  </script>
  
  <style scoped>
  .asynchrone {
    margin-bottom: 20px;
  }
  </style>