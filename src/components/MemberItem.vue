<script setup lang="ts">
const props = defineProps({ member: Object });
const emits = defineEmits(['deleteMember'])

const removeMember = (id: String) => {
    emits('deleteMember', id);
}
</script>

<template>
    <div class="item">
        <p>编码：{{ props.member.code }}</p>
        <p>名称：{{ props.member.name }}</p>
        <p><button @click="removeMember(props.member.id)">删除</button></p>
    </div>

</template>

<style scoped>
.item {
    width: 100px;
    background-color: aqua;
    float: left;
    margin-left: 5px;
    padding: 5px;
}
</style>