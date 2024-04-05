<script setup lang="ts">
import orgApi from '../api/org'
import { ref, onMounted } from 'vue'
import type Node from 'element-plus/es/components/tree/src/model/node'

// const data = ref<Tree[]>([])

interface Tree {
    id:string
    label: string
    children?: Tree[]
}

onMounted(() => {
//   orgApi.query().then((users) => {
//     console.log('orgs', users)
//     users.forEach((user) => {
//         var temp : Tree = {
//             id: user.id,
//             label: user.name,
//             children: []
//         }
//         data.value.push(temp)
//     })
//   })
})


const loadNode = (node: Node, resolve: (data: Tree[]) => void) => {
    if (node.level === 0) {
        orgApi.query().then((users) => {
            return resolve(users.map((user) => {
                return {
                    id: user.id,
                    label: user.name,
                    children: []
                }
            }))
        })
    } else {
        orgApi.query(node.data.id).then((users) => {
            console.log('node.data.id', node.data.id)
            console.log('orgs', users)
            return resolve(users.map((user) => {
                return {
                    id: user.id,
                    label: user.name,
                    children: []
                }
            }))
        })
    }
   
}


</script>

<template>
   <el-tree
        style="max-width: 600px"
        :load="loadNode"
        lazy
    /> 
</template>

<style scoped>
</style>