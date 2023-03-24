<template>
    <div class="option_container">
        <h4>{{ option.title }}</h4>
          <div class="option_buttons">
            <button 
            v-for="(value, index) of option.buttons"
            :key="value"
            class="option"
            :class="computedButtonClasses(value, index)"
            @click="options[option.category] = value"
            >{{ value }}</button>
          </div>
      </div>
</template>

<script setup lang="ts">
import {Gender, Popularity, Length} from '@/data'

interface OptionProps {
    option: {
        title: string; 
        category: string;
        buttons: Gender[] | Popularity[] | Length[];
    };
    options: {
        gender: Gender;
        popularity: Popularity;
        length: Length
    }
}

const props = defineProps<OptionProps>();

const computedButtonClasses = (value: any, index: Number) => {
  const classNames = [];

  if (props.options[props.option.category] === value) {
    classNames.push('option_active')
  }

  if (index === 0) classNames.push('option_left')
  if (index === props.option.buttons.length - 1) classNames.push('option_right')

  return classNames.join(' ');
}


</script>

<style scoped>
.option_container {
    margin-bottom: 2rem;
  }
  .option {
    background: white;
    outline: .15rem solid rgb(249, 87, 89);
    border: none;
    padding: .75rem;
    width: 12rem;
    font-size: 1rem;
    color: rgb(27, 60, 138);
    font-weight: 200;
    cursor: pointer;
  }
  .option_left {
    border-radius: 1rem 0 0 1rem;
  }
  .option_right {
    border-radius: 0 1rem 1rem 0 ;
  }
  .option_active {
    background: rgb(249, 87, 89);
    color: white;
  }
  .primary {
    background: rgb(249, 87, 89);
    color: white;
    border-radius: 1.5rem;
    border: none;
    padding: .75rem 4rem;
    font-size: 1rem;
    margin-top: 1rem;
    cursor: pointer; 
    }
</style>