<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <li 
            v-for="transaction in transactions" 
            :class="transaction.amount > 0 ? 'plus' : 'minus'" 
            :key="transaction.id"
            >
            {{transaction.text}} <span>{{ transaction.amount }}</span><button class="delete-btn" @click="deleteTransaction(transaction.id)">x</button>
        </li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';

const props = defineProps({
    transactions: {
        type: Array,
        required: true
    }
})

const emit = defineEmits(['transactionDeleted']);


const deleteTransaction = (id) => {
    emit('transactionDeleted', id)
}

</script>