<template>
    <briup-fulllayout title="新增地址">
    <div>
        <van-cell-group>
            <van-field v-model="form.telephone" placeholder="请输入手机号" />
            </van-cell-group>
        <van-cell-group>
            <van-field v-model="form.pca" placeholder="省市区" />
            </van-cell-group>
        <van-cell-group>
            <van-field v-model="form.address" placeholder="详细地址" />
            </van-cell-group>
    </div>
    <van-button block type="primary" @click="submitHandler">保存</van-button>
    </briup-fulllayout>
</template>
<script>
import{post} from '../../../http/axios'
import {mapState} from 'vuex'
export default {
    data(){
        return{
      form:{}
        }
    
    },
    methods:{
        submitHandler(){
            let url="/address/saveOrUpdate"
            this.form.customerId=this.info.id;
            post(url,this.form).then((response)=>{
                this.$router.go(-1);
            })
        }
    },
    computed:{
        ...mapState('user',['info'])
    }
    
}
</script>