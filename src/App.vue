<script setup lang="ts">
import { reactive } from 'vue'
import ProjectMember from './components/ProjectMember.vue';

const project = reactive({
    projectName: "User Base"
});

const updateProject = () => {
    const date = new Date();
    project.projectName = date.toLocaleTimeString();
}
</script>

<template>
    <h1>项目信息</h1>
    项目名称：<input v-model="project.projectName" /> &nbsp;
    <button @click="updateProject">更新</button>
    <br />
    <ProjectMember :memberCount="5 - 2"></ProjectMember>

</template>

<style scoped></style>
