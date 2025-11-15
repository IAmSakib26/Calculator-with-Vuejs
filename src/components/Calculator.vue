<script setup>
    import { ref } from 'vue'

    const currentValue = ref('')
    const previousValue = ref('')
    const operator = ref('')
    const equal = ref('')

    const updateDisplay = (value) => {
        currentValue.value = currentValue.value + value
        console.log(currentValue.value);
    }
    const operatorSelected = (value) => {
        operator.value = value
        previousValue.value = currentValue.value
        currentValue.value = ''
        console.log(operator.value, previousValue.value);
    }
    const equals = () => {
        equal.value = eval(previousValue.value + operator.value + currentValue.value)
        currentValue.value = equal.value.toString()
        console.log(equal.value)
    }
</script>
<template>
    <div class="flex justify-center items-center h-screen m-0 bg-[#d2daf5c5]">
        <div class="bg-white rounded-2xl p-5">
            <div class="w-full flex justify-center items-center gap-2.5 mb-2.5">
                <input type="text" id="display" :value = "currentValue || 0" readonly class="w-40 h-12 text-xl text-right mb-2.5 p-3 bg-[#dbefdf] border-none rounded-lg">
                <button @click="currentValue = ''" class="w-[50px] h-[50px] border-none rounded-full bg-[#f84033] text-white mb-2.5">AC</button>
            </div>
            <div class="grid grid-cols-4 gap-2.5">
                <button @click="updateDisplay('7')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="7">7</button>
                <button @click="updateDisplay('8')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="8">8</button>
                <button @click="updateDisplay('9')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="9">9</button>
                <button @click="operatorSelected('+')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#ede467] text-black flex justify-center items-center" data-value="+">+</button>
                <button @click="updateDisplay('4')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="4">4</button>
                <button @click="updateDisplay('5')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="5">5</button>
                <button @click="updateDisplay('6')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="6">6</button>
                <button @click="operatorSelected('-')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#ede467] text-black flex justify-center items-center" data-value="-">-</button>
                <button @click="updateDisplay('1')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="1">1</button>
                <button @click="updateDisplay('2')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="2">2</button>
                <button @click="updateDisplay('3')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="3">3</button>
                <button @click="operatorSelected('*')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#ede467] text-black flex justify-center items-center" data-value="*">*</button>
                <button @click="updateDisplay('0')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value="0">0</button>
                <button @click="updateDisplay('.')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#92e9fa]" data-value=".">.</button>
                <button @click="equals" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#c271c5] text-white">=</button>
                <button @click="operatorSelected('/')" class="w-[50px] h-[50px] text-lg border-none rounded-full cursor-pointer bg-[#ede467] text-black flex justify-center items-center" data-value="/">/</button>
            </div>
        </div>
    </div>
</template>