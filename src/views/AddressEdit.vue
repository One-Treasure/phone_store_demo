<template>
    <van-address-edit
            :area-list="areaList"
            show-delete
            :address-info="addressInfo"
            save-button-text="修改"
            @save="onSave"
            @delete="onDelete"
    />
</template>

<script>
    import AreaList from '../api/area';
    import { Toast } from 'vant';
    export default {
        name: "AddressEdit",
        created() {
          let data = JSON.parse(this.$route.query.item)
          this.addressInfo = data
          /*找到地址文本中的区或者县，然后从区或县的后一位开始截取，详细地址中就不会出现和地区重复的字符串了*/
          let index = data.address.indexOf('区')
          if (index < 0) index = data.address.indexOf('县')
          this.addressInfo.addressDetail = data.address.substring(index+1)
        },
        data() {
            return {
                areaList: AreaList,
                addressInfo: {
                    name: '张三',
                    tel: '123',
                    areaList: '130105',
                    addressDetail: '浙江省杭州市西湖区文三路 138 号东方通信大厦 7 楼 501 室'
                }
            };
        },
        methods: {
            onSave(item) {
                let instance = Toast('修改成功');
                setTimeout(() => {
                    instance.close()
                    this.$router.push('/addressList')
                },1000)
            },
            onDelete() {
                history.go(-1)
            },
        },
    }
</script>

<style scoped>

</style>