<template>
    <div class="search">
        <div class="input-search1">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Amazon</button>
            <b>Amazon</b>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach2">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Microsoft</button>
            <b>Microsoft</b>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach3">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">LPI</button>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach4">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Cisco</button>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach5">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">CompTIA</button>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach6">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Google</button>
            <a>展示:{{ detail }}</a>
        </div>

        <div class="input-serach7">
            <input type="file" name="file" @change="fileChange" />
            <button @click="submit">Oracle</button>
            <a>展示:{{ detail }}</a>
        </div>
    </div>
</template>

<script>
import axios from "axios"
let _fileObj;
export default {
    name: "HelloWorld",
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

            // 获取下一个<a>元素
            const nextSibling = $event.target.nextElementSibling;
            // 获取下一个<a>元素的文本内容
            const text = nextSibling.innerText;
            // 在这里使用下一个<a>元素的文本内容（"Microsoft"）
            console.log(text);
            var p1 = _fileObj.name
            var url = 'http://localhost:3000/nativaRoute/read/' + text + '/' + p1 + '/xxxx'
            // 配置url参数
            // let _formDate = new FormData();
            // _formDate.append("file", _fileObj);
            var params = {
                _fileObj
            }

            // 发起axios请求接口
            axios.get(url, { params })
                .then(res => {
                    // 得到后台数据
                    console.log(res.data);
                    // #将json数据取出来,一个一个的按照位置填充到模板
                    this.msg = 22;
                    this.detail = res.data;
                    console.log("11111111111111" + params._fileObj.name)
                }).catch(err => {
                    alert('链接错误')
                })

            // axios.get("http://localhost:3000/nativaRoute/search/input/aa/dd", _formDate);
        }
    }

}
</script>


<style scoped lang="stylus">
.search {
    line-height:50px;
}
</style>