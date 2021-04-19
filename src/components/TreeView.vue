<template>
  <div class="treeview">
    <p>Volba ikon:</p>
    <input type="text" placeholder="Ikona pro soubory" v-model="icons['file']" />
    <input type="text" placeholder="Ikona pro složky" v-model="icons['folder']" />
    <ul>
      <TreeNode :icons="icons" :node="tree" />
    </ul>
  </div>
</template>

<script>
import TreeNode from "./TreeNode";

export default {
  name: "TreeView",
  components: {
    TreeNode,
  },
  data() {
    return {
      tree: [],
      icons: {
        file: "file",
        folder: "folder",
      },
    };
  },
  created() {
    this.tree = [
      {
        type: "file",
        title: "Soubor 1",
      },
      {
        type: "file",
        title: "Soubor 2",
      },
      {
        type: "folder",
        title: "Složka 1",
        content: [
          {
            type: "file",
            title: "Soubor 3",
          },
          {
            type: "folder",
            title: "Složka 2",
            content: [
              {
                type: "file",
                title: "Soubor 4",
              },
              {
                type: "folder",
                title: "Složka 3",
                content: [
                  {
                    type: "file",
                    title: "Soubor 5",
                  },
                  {
                    type: "file",
                    title: "Soubor 6",
                  },
                ],
              },
            ],
          },
          {
            type: "folder",
            title: "Složka 4",
            content: [
              {
                type: "file",
                title: "Soubor 7",
              },
              {
                type: "file",
                title: "Soubor 8",
              },
            ],
          },
        ],
      },
    ];
  },
};
</script>

<style scoped>
p {
  font-size: 20px;
  margin-bottom: 0.5rem;
}

input {
  padding: 0.5rem;
  font-size: 16px;
  border-radius: 0.5rem;
  border: 1px solid black;
  outline: none;
  margin-bottom: 0.5rem;
}
</style>
