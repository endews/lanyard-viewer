<template>
    <div>
        <p class="text-3xl">{{ userName }}</p>
    </div>
</template>

<script>
export default {
    name: "MainContent",
    props: ["userName"],
}
</script>