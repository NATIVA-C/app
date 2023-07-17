<template>
    <div class="search">
        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button  class="bnt" @click="submit">Amazon</button>
            <b class="text-b">Amazon</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Microsoft</button>
            <b class="text-b">Microsoft</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">LPI</button>
            <b class="text-b">LPI</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Cisco</button>
            <b class="text-b">Cisco</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">CompTIA</button>
            <b class="text-b">CompTIA</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Google</button>
            <b class="text-b">Google</b>
        </div>

        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Oracle</button>
            <b class="text-b">Oracle</b>
        </div>
        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Salesforce</button>
            <b class="text-b">Salesforce</b>
        </div>
        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">ServiceNow</button>
            <b class="text-b">ServiceNow</b>
        </div>
        <div class="input-search">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">CKA</button>
            <b class="text-b">CKA</b>
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

.bnt{
    padding auto;
}
.input-search{
    margin-bottom: 11px;
}
.text-b{
    margin-left: 20px;
}
</style>