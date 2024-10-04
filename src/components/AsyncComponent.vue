<template>
    <button class= "buttonDenied" :disabled="isPending" :color="color" @click="handleClick">
      <a v-if="isPending"> Loading... </a>
        Click me but not to fast
    </button>
  </template>
  
  <script>
  export default 
  {
      name: 'AsyncComponent',
      
    data() 
    {
      return {
        isPending: false,
      };
    },
  
    methods: 
    {
      handleClick() 
      {
        const originalOnClick = this.$attrs.onClick;
        if (originalOnClick && typeof originalOnClick === 'function') 
        {
            this.isPending = true;
            originalOnClick().finally(() => 
            {
                this.isPending = false; 
            });
        }
      }
    }
  };
  </script>
  <style>
    .buttonDenied {
    height: 40px;
    width: 200px;
    padding: 10px 20px;
    font-size: 16px;
    font-family: Arial, sans-serif;
    border: 2px solid #7b4b5d;
    border-radius: 4px;
    background-color: #fff;
    color: #7b4b5d;
    cursor: pointer;
    transition: all 0.3s ease;
    }
  </style>