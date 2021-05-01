<template>
    <van-address-edit
            :area-list="areaList"
            show-delete
            @save="onSave"
            @delete="onDelete"
    />
</template>

<script>
    import AreaList from '../api/area';
    import { Toast } from 'vant';
    export default {
        name: "AddressNew",
        data() {
            return {
                areaList: AreaList
            };
        },
        methods: {
            onSave(item) {
                let instance = Toast('添加成功');
                setTimeout(() =>{
                    instance.close();
                    this.$router.push('addressList')
                },1000)
            },
            onDelete() {
                history.go(-1)/*退回上一页*/
            },
        },
    }
</script>

<style scoped>

</style>