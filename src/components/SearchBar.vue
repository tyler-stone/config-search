<template>
<div class="container">
    <div class="row">
        <div class="u-full-width" style="margin-top: 25px;">
        <h4>GM Config Search</h4>
        <div class="twelve columns">
            <input class="u-full-width" type="text" v-bind:value="value" v-on:input="$emit('input', $event.target.value)" placeholder="Search for anything... with regex!">
        </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    props: ['value']
};
</script>

<style>
</style>
