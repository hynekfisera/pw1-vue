<template>
  <div class="node">
    <li class="file" :key="tree.title" v-for="tree in node.filter((tree) => tree.type == 'file')"><i :class="['fas fa-' + icons['file']]"></i> {{ tree.title }}</li>
    <li class="folder" :key="tree.title" v-for="tree in node.filter((tree) => tree.type == 'folder')">
      <span><i :class="['fas fa-' + icons['folder']]"></i> {{ tree.title }}</span>
      <ul>
        <TreeNode :icons="icons" :node="tree.content" />
      </ul>
    </li>
  </div>
</template>

<script>
export default {
  name: "TreeNode",
  props: {
    node: Array,
    icons: Object,
  },
};
</script>

<style scoped>
* {
  font-size: 18px;
  list-style: none;
}
i {
  font-size: 16px;
}
li {
  margin-top: 5px;
}
.node {
  margin-left: 2em;
}
.file {
  font-weight: 500;
}
.folder span {
  font-weight: 700;
}
</style>
