<template>
    <div class="search">
        <div class="input-search1">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Amazon</button>
            <b>Amazon</b>
        </div>

        <div class="input-serach2">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Microsoft</button>
            <b>Microsoft</b>
        </div>

        <div class="input-serach3">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">LPI</button>
            <b>LPI</b>
        </div>

        <div class="input-serach4">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Cisco</button>
            <b>Cisco</b>
        </div>

        <div class="input-serach5">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">CompTIA</button>
            <b>CompTIA</b>
        </div>

        <div class="input-serach6">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Google</button>
            <b>Google</b>
        </div>

        <div class="input-serach7">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Oracle</button>
            <b>Oracle</b>
        </div>
        <div class="input-serach7">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Salesforce</button>
            <b>Salesforce</b>
        </div>
        <div class="input-serach7">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">ServiceNow</button>
            <b>ServiceNow</b>
        </div>
        <div class="input-serach7">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">CKA</button>
            <b>CKA</b>
        </div>
    </div>
</template>

<script>
import axios from "axios"
let _fileObj;
export default {
    name: "read",
    data() {
        return {
            datalist: '11',
            msg: '',
            detail: 'res.data'
        }
    },
    methods: {
        fileChange(e) {
            let file = e.target.files[0]
            _fileObj = file;
        },
        async submit($event) {
            // 获取下一个<b>元素
            const nextSibling = $event.target.nextElementSibling;
            // 获取下一个<a>元素的文本内容
            const fileDir = nextSibling.innerText;
            // 在这里使用下一个<a>元素的文本内容（"Microsoft"）
            console.log(fileDir);
            var fileName = _fileObj.name
            var url = 'http://localhost:3000/nativaRoute/read/' + fileDir + '/' + fileName + '/xxxx'
            // 配置url参数
            var params = {
                _fileObj
            }
            // 发起axios请求接口
            axios.get(url, { params })
                .then(res => {
                    // 得到后台数据
                    console.log(res.data);
                    // over
                    alert(res.data);
                }).catch(_ => {
                    alert('链接错误')
                })
        }
    }
}
</script>


<style scoped lang="stylus">
.search {
    line-height:50px;
}
</style>