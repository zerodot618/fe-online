<script setup lang="ts">
import orgApi from '../api/org'
import { ref, onMounted } from 'vue'


onMounted(() => {
  orgApi.query().then((users) => {
    console.log('orgs', users)
    data.value = users
  })
})

interface Tree {
    id:string
    name: string
    children?: Tree[]
}

const handleNodeClick = (data: Tree) => {
  console.log(data)
}

const data = ref<Tree[]>([])

// const data: Tree[] = [
//   {
//     label: 'Level one 1',
//     children: [
//       {
//         label: 'Level two 1-1',
//         children: [
//           {
//             label: 'Level three 1-1-1',
//           },
//         ],
//       },
//     ],
//   },
//   {
//     label: 'Level one 2',
//     children: [
//       {
//         label: 'Level two 2-1',
//         children: [
//           {
//             label: 'Level three 2-1-1',
//           },
//         ],
//       },
//       {
//         label: 'Level two 2-2',
//         children: [
//           {
//             label: 'Level three 2-2-1',
//           },
//         ],
//       },
//     ],
//   },
//   {
//     label: 'Level one 3',
//     children: [
//       {
//         label: 'Level two 3-1',
//         children: [
//           {
//             label: 'Level three 3-1-1',
//           },
//         ],
//       },
//       {
//         label: 'Level two 3-2',
//         children: [
//           {
//             label: 'Level three 3-2-1',
//           },
//         ],
//       },
//     ],
//   },
// ]

const defaultProps = {
  children: 'children',
  label: 'label',
}
</script>

<template>
   <el-tree
        style="max-width: 600px"
        :data="data"
        :props="defaultProps"
        @node-click="handleNodeClick"
    /> 
</template>

<style scoped>
</style>