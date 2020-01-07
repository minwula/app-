<template>
<briup-fulllayout title="常用地址">
<van-list>
 <van-cell
    v-for="item in addresses"
    :key="item.id"
    :title="item.province+' '+item.city+' '+item.area+' '+item.address"
  />
</van-list>
<van-button type="default" @click="toAddressEditHandler" block>添加</van-button>
</briup-fulllayout>

</template>
<script>
import{get} from '../../../http/axios'
import{mapState} from 'vuex'
export default {
    data(){
        return{
            addresses:[]
        }
    },
    computed:{//计算属性
    //将状态机中的user
        ...mapState("user",["info"])
    },
    created(){
    this.loadAddress();
    },
    methods:{
        loadAddress(){
            let id=this.info.id;
            let url="/address/findByCustomerId?id="+id;
            get(url).then((response)=>{
                this.addresses=response.data;
            })
        },
        toAddressEditHandler(){
            this.$router.push("/manager/address_edit");
        }
    }
    
}
</script>