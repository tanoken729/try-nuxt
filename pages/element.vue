<template>
    <div style="padding: 30px">
        <el-button @click="visible = true">Button</el-button>
        <el-dialog :visible.sync="visible" title="確認">
            <p>Try Element</p>
        </el-dialog>
    </div>
</template>

<script>
export default ({
    data() {
        return {
            visible: false
        }
    },
})
</script>
