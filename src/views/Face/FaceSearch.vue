<template>
    <div class="container">
        <!-- 1.人员姓名查询框 -->
        <div class="searchBox">
            <span>人员姓名</span>
            <el-select v-model="value" class="selectBox" placeholder="请输入人员姓名">
                <el-option
                    v-for="item in options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                />
            </el-select>
            <el-button type="primary" class="btn1">查询</el-button>
            <el-button type="danger" class="btn2">删除</el-button>
        </div>
        <!-- 2.管理采集表 -->
        <div class="searchResult">
            <span>管理采集表</span>
            <el-table :data="tableData" class="caijiTable"  fit="true" highlight-current-row="true">
                <el-table-column fixed prop="date" label="采集时间" width="182" />
                <el-table-column prop="front" label="人脸正面" width="220">
                    <template #default>
                        <img class="img0" :src="img1_src"/>
                    </template>
                </el-table-column>
                <el-table-column prop="left" label="人脸左15" width="220">
                    <template #default>
                        <img class="img0" :src="img2_src"/>
                    </template>
                </el-table-column>
                <el-table-column prop="right" label="人脸右15" width="220">
                    <template #default>
                        <img class="img0" :src="img3_src"/>
                    </template>
                </el-table-column>
                <el-table-column prop="operate" label="操作" width="200">
                    <template #default>
                        <el-button type="primary" text="primary">查询</el-button>
                        <el-button type="danger" text="danger">删除</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </div>
        <!-- 3.数据库查询出的人脸展示 -->
        <div class="faceShow">
            <div class="videoImg">
                <div>
                    <span>人脸正面</span>
                    <img class="img1 " :src="img1_src"/>
                </div>
                <div>
                    <span>人脸左15度</span>
                    <img class="img1 " :src="img2_src"/>
                </div>
                <div>
                    <span>人脸右15度</span>
                    <img class="img1 " :src="img3_src"/>
                </div>
            </div>
        </div>
        <!-- 4.数据库查询出的人脸对应的特征展示 -->
        <div class="featureShow">
            <div class="featureImg">
                <div>
                    <span>特征提取</span>
                    <img class="img1 " :src="img4_src"/>
                </div>
                <div>
                    <span>特征提取</span>
                    <img class="img1 " :src="img5_src"/>
                </div>
                <div>
                    <span>特征提取</span>
                    <img class="img1 " :src="img6_src"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import { ref } from 'vue'
export default{
    setup(){
        const value = ref('')
        const options = [
            {
                value: 'Option1',
                label: 'Option1',
            },
            {
                value: 'Option2',
                label: 'Option2',
            },
            {
                value: 'Option3',
                label: 'Option3',
            },
        ]
        // 定义表格数据
        const tableData = [
            {
                date: '2023-03-30',
                front: '',
                left: '',
                right: '',
                operate: '',
            },
            {
                date: '2023-03-30',
                front: '',
                left: '',
                right: '',
                operate: '',
            },
            {
                date: '2023-03-30',
                front: '',
                left: '',
                right: '',
                operate: '',
            },
        ]
        //定义图片实例
        const img1_src = ref(require('@/assets/img/moren.webp'))
        const img2_src = ref(require('@/assets/img/moren.webp'))
        const img3_src = ref(require('@/assets/img/moren.webp'))
        const img4_src = ref(require('@/assets/img/moren.webp'))
        const img5_src = ref(require('@/assets/img/moren.webp'))
        const img6_src = ref(require('@/assets/img/moren.webp'))

        return{
            value,
            options,
            tableData,
            img1_src,
            img2_src,
            img3_src,
            img4_src,
            img5_src,
            img6_src
        }
    }
}
</script>

<style scoped>
.container{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
}
.searchBox{
    display: flex;
    width:89%;
    margin-top:1%;
    margin-left:5%;
    padding:5px;
    border: 1px solid rgb(242, 238, 238);
    background-color: rgb(242, 238, 238);
}
.searchBox > span{
    margin-left:3%;
    margin-top:1%;
    font-size:16px;
}
.selectBox{
    margin-left:5%;
}
.btn1{
    margin-left:38%;
    margin-right:3%;
}
.btn2{
    margin-right:5%;
}
.searchResult{
    display: flex;
    flex-direction: column;
    width:90%;
    margin-top:1%;
    margin-left:5%;
    border: 1px solid rgb(242, 238, 238);
    background-color: rgb(242, 238, 238);
}
.searchResult > span{
    font-size:18px;
    margin-left:2%;
    margin-top:1%;
    font-weight: 700;
}
.caijiTable{
    width: 90%;
    height:88%;
    margin-left:4%;
    margin-top:1%;
    margin-bottom: 1%;
    font-size: 14px;
    border:1px solid rgb(242, 238, 238);
}
.img0{
    width: 30%;
    height:15%;
    display: flex; 
    align-items: center
}
.faceShow,.featureShow{
    display: flex;
    width:90%;
    margin-left:5%;
    margin-top:1%;
    border: 1px solid rgb(242, 238, 238);
    background-color: rgb(242, 238, 238);
}
.videoImg,.featureImg{
    display: flex;
    width: 90%;
    height:55%;
    border:2px solid rgb(242, 238, 238);
    margin-left:4%;
    align-items: center;
    justify-content: space-around;
  }
  .videoImg > div,.featureImg > div{
    display: flex;
    flex-direction: column;
    align-items: center;
    font-size:16px;
    margin:3px;
  }

  .img1{
    width: 45%;
    height: 65%;
    border:1px solid #1b1c1d;
    margin-top:3px;
  }
</style>