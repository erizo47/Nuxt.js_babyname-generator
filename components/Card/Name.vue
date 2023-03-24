<template>
    <div class="card">
        <h4>{{ name }}</h4>
        <div class="close_card" @click="removeName">
            <p>x</p>
        </div>
    </div>
</template>

<script setup lang="ts">

interface NameProps {
    name: string,
    index: number
}

const props = defineProps<NameProps>();

const emit = defineEmits(["remove"]);

const removeName = () => {
    emit('remove', props.index)
}
</script>

<style scoped>
.card {
  background-color: rgb(84, 119, 201);
  width: 22%;
  color: white;
  border-radius: 1rem;
  margin-right: 0.5rem;
  margin-bottom: 1rem;
  position: relative;
}
.close_card {
    width: 1rem;
    height: 1rem;
    background: white;
    border-radius: 2rem;
    position: absolute;
    top: 8%;
    left: 88%;

}
.card p {
    position: absolute;
    top: -17px;
    left: 4px;
  cursor: pointer;
  color: rgb(0, 150, 255);
}
</style>