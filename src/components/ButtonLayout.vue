<template>
  <div>

    <button :class="{disabled: isDisabled}" class="button" @click="handleClick">
      {{ isDisabled ? 'Disabled' : 'Click Me' }}
    </button>

    <button class="button" :style="{ width: buttonWidth + 'px', height: buttonHeight + 'px' }"
      :class="{ bigger: isBigger, max: isMax }" @click="BiggerWeight"> Be bigger
    </button>

    <button class ="button" :style="buttonStyle('primary')" @mouseover="isHovered1 = true" @mouseleave="isHovered1 = false" 
      @focus="isFocused1 = true">
      {{ isHovered1 ? 'Hovered' : isFocused1 ? 'Focused' : 'Default'}}
      First Color
    </button>

    <button class="button" :style="buttonStyle('warn')" @mouseover="isHovered2 = true" @mouseleave="isHovered2 = false" 
      @focus="isFocused2 = true" >
      {{ isHovered2 ? 'Hovered' : isFocused2 ? 'Focused' : 'Default'}}
      Second Color
    </button>

    <button class="button" :style="buttonStyle('danger')" @mouseover="isHovered3 = true" @mouseleave="isHovered3 = false" 
      @focus="isFocused3 = true">
      {{ isHovered3 ? 'Hovered' : isFocused3 ? 'Focused' : 'Default'}}
      Third Color
    </button>

  </div>
</template>

<script>
export default 
{
  name: 'ButtonLayout',
  data() 
  {
    return {
      isDisabled: false,
      isBigger: false,
      isMax: false,
      buttonWidth: 200,
      buttonHeight: 40,
      maxSize: 300,

      isHovered1: false,
      isFocused1: false,
      isHovered2: false,
      isFocused2: false,
      isHovered3: false,
      isFocused3: false,
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
  computed: 
  {
    buttonStyle() 
    {
      return (color) => 
      {
        const colorPalette = 
        {
          primary: { bg: '#42b983', hoverBg: '#4cce93', focusBorder: '#47d696' },
          warn: { bg: '#ff5722', hoverBg: '#ff7043', focusBorder: '#ff8a65' },
          danger: { bg: '#e53935', hoverBg: '#ef5350', focusBorder: '#e57394' },
        };

        const selectedColor = colorPalette[color];

        const isHovered = this[`isHovered${color === 'primary' ? '1' : color === 'warn' ? '2' : color === 'danger' ? '3' : '4'}`];
        const isFocused = this[`isFocused${color === 'primary' ? '1' : color === 'warn' ? '2' : color === 'danger' ? '3' : '4'}`];
        const bgColor = isHovered ? selectedColor.hoverBg : selectedColor.bg;
        const borderColor = isFocused ? selectedColor.focusBorder : 'transparent';

        return {
          backgroundColor: bgColor,
          border: `2px solid ${borderColor}`,
          padding: '10px 20px',
          color: '#fff',
          cursor: 'pointer',
        };
      };
    },
  },
};
</script>

<style scoped>
.button {
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

.button:not(:disabled):hover {
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

.button:disabled {
  background-color: #e0e0e0;
  color: #b0b0b0;
  border-color: #b0b0b0;
  cursor: not-allowed;
  transform: none;
  box-shadow: none;
}
</style>
