<template>
    <h2>项目成员</h2>
    <div>数量：{{ memberObj.memberList.length }}</div>
    ID : <input v-model="member.id" />
    编码：<input v-model="member.code" />
    名称：<input v-model="member.name" />
    <button @click="addMember">添加成员</button>
    <div>
        <MemberItem v-for="item in memberObj.memberList" :member="item" @deleteMember="delMember" />
    </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue';
import MemberItem from './MemberItem.vue';

const props = defineProps({ memberCount: Number });
let memberObj = reactive({ "memberList": [] });
for (let i = 1; i <= props.memberCount; i++) {
    memberObj.memberList.push({ "id": i.toString(), "code": "DE-" + i, "name": "张氏" + i });
}

const member = reactive({ id: '', code: '', name: '' });
function addMember() {
    memberObj.memberList.push({ ...member })
    member.id = '';
    member.code = '';
    member.name = '';
}
function delMember(id: String) {
    memberObj.memberList = memberObj.memberList.filter(vo => vo.id != id);
}

</script>