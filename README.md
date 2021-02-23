# 私有代码块(gjl) for Visual Studio Code
集成自定义代码块

输入 theTemplate
回车展示
<ThePlanOrg v-model="modelObj.parentId" styleOption="width:300px"></ThePlanOrg>
<template>
<a-select
v-model="valueCopy"
v-on="$listeners"
v-bind="$attrs"
:style="$styleOption"
@change="change"
>
<a-select-option v-for="t in list" :key="t.id">
{{ t.name }}
</a-select-option>
</a-select>
</template>
<script>
import {  getCounorg as getFun } from "@/api/basicInformation.js";
export default {
model: {
prop: "value",
event: "change"
},
props: {
value: {},
styleOption: {
default() {
return `width:300px`;
}
}
},
data() {
return {
list: []
};
},
mounted() {
this.getFun();
},
computed: {
valueCopy: {
get() {
return this.value;
},
set(val) {
this.emit("change", val);
}
}
},
methods: {
change(val) {
this.$emit("change", val);
},
getFun() {
getFun({}).then(res => {
this.list = res.data || [];
 });
}
}
};
</script>
<style scoped lang="less">
</style>