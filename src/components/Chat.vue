<script setup>
const listaCompleja = [
    { id: 1, lista1: 9, relleno: { id2: 1.1, base2: { id3: 1.3, elem: [1, 2, 3, 4] } } },
    { id: 2, lista1: 8, relleno: { id2: 2.2, base2: { id3: 2.4, elem: [2, 3, 4, 1] } } },
    { id: 3, lista1: 7, relleno: { id2: 3.3, base2: { id3: 3.3, elem: [3, 4, 2, 1] } } },
    { id: 4, lista1: 6, relleno: { id2: 4.4, base2: { id3: 4.4, elem: [4, 1, 2, 3] } } },
    { id: 5, lista1: 5, relleno: { id2: 5.5, base2: { id3: 5.3, elem: [1, 4, 3, 2] } } },
    { id: 6, lista1: 4, relleno: { id2: 6.6, base2: { id3: 6.4, elem: [2, 3, 4, 1] } } },
]
</script>

<template>
    <div>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Número</th>
                    <th>ID de Relleno</th>
                    <th>ID de Base 2</th>
                    <th>Elementos</th>
                </tr>
            </thead>

            <tbody>
                <tr v-for="item in listaCompleja" :key="item.id">
                    <td>{{ item.id }}</td>
                    <td>{{ item.lista1 }}</td>
                    <td>{{ item.relleno.id2 }}</td>
                    <td>{{ item.relleno.base2.id3 }}</td>
                    <td>{{ item.relleno.base2.elem.join('-') }}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>