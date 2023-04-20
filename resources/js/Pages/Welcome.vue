<script setup>
import { Head, Link } from '@inertiajs/vue3';
import { inject,  ref, onMounted } from 'vue';

const $cookies = inject('$cookies');

const old_cookie = ref()
const new_cookie = ref()



old_cookie.value = $cookies.get('cookie-name');

onMounted(() => {
    axios
        .get('/get-cookie')
        .then(response => {
            new_cookie.value = $cookies.get('cookie-name');
        });
});

</script>

<template>
    <Head title="Welcome" />

    <div>
        <p>Old cookie: {{ old_cookie }}</p>
        <p>New cookie: {{ new_cookie }}</p>
    </div>
</template>
