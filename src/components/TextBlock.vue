<template>
    <div v-for="(row, idx) in textArr"
         :key="'row_' + idx"
        class="row">
        {{row}}
    </div>
</template>
<script setup>
const props = defineProps({
    rowText: String
})

const textArr = props.rowText.split('\n')

</script>
<style scoped>
.row {
    line-height: 3.1rem;
    font-weight: 500;
}
.row:nth-child(even) {
    margin-left: 4.5rem;
}
</style>