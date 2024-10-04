<template>
  <div>

    <button :class="{disabled: isDisabled}" class="button" @click="handleClick">
      {{ isDisabled ? 'Disabled' : 'Click Me' }}
    </button>

    <button class="button" :style="{ width: buttonWidth + 'px', height: buttonHeight + 'px' }"
      :class="{ bigger: isBigger, max: isMax }" @click="BiggerWeight"> Be bigger
    </button>
  </div>
</template>

<script>
export default 
{
  name: 'ButtonLayout',
  data() 
  {
    return{
      isDisabled: false,
      isBigger: false,
      isMax: false,
      buttonWidth: 120,
      buttonHeight:40,
      maxSize: 200, 
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
        this.isBigger = true;
        this.buttonWidth += 20;
        this.buttonHeight += 10;

        if (this.buttonWidth >= this.maxSize && this.buttonHeight >= this.maxSize) 
        {
          this.isMax = true;
        }
      }
    },
  },
};
</script>

<style>
.button 
{
  height: 40px;
  width: 120px;
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

.button:not(:disabled):hover 
{
  background-color: #7b4b5d;
  color: #fff;
  transform: scale(1.05);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.button:focus {
  outline: none;
  border-color: #a77283;
  box-shadow: 0 0 0 3px rgba(123, 75, 93, 0.3);
}

.button:disabled 
{
  background-color: #e0e0e0;
  color: #b0b0b0;
  border-color: #b0b0b0;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}
</style>
