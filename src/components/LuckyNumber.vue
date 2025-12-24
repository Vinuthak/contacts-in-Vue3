<template>
    <div class="float-end">
        <button class="btn btn-outline-danger" @click="generateNumber()">
            <span v-if="luckyNumber===0">
                Generate Lucky Number<br>
                Range(1 - {{ maxNumber }})
            </span>
            <span v-else>Lucky number is {{ luckyNumber }}<br>
            Click to generate Lucky Number</span>
        </button>
    </div>
</template>

<script setup>
import { ref, inject } from 'vue';

    const luckyNumber = ref(0);

    const maxNumber = inject('maxLuckyNumber');
    function generateNumber(){
        console.log(maxNumber);
        console.log(typeof(maxNumber));
        luckyNumber.value = Math.floor(Math.random() * maxNumber.value);
    }

    
</script>