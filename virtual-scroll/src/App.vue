
<template>
    <div class="card">
        <DataTable :value="cars" scrollable scrollHeight="400px" :virtualScrollerOptions="{ itemSize: 46 }" tableStyle="min-width: 50rem">
            <Column field="id" header="Id" style="width: 20%"></Column>
            <Column field="vin" header="Vin" style="width: 20%"></Column>
            <Column field="year" header="Year" style="width: 20%"></Column>
            <Column field="brand" header="Brand" style="width: 20%"></Column>
            <Column field="color" header="Color" style="width: 20%"></Column>
        </DataTable>
    </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import { CarService } from '@/service/CarService';

const cars = ref();

onMounted(() => {
    cars.value = Array.from({ length: 100000 }).map((_, i) => CarService.generateCar(i + 1));
});
</script>
