<template>
  <div>
    <div class="block">
      <el-row>
        <el-button :plain="true" @click="open('eri')">
          <img src="~/static/img/eri.jpg">
          <p>eri</p>
        </el-button>
        <el-button :plain="true" @click="open('eri2')">
          <img src="~/static/img/eri2.jpg">
          <p>eri2</p>
        </el-button>
        <el-button :plain="true" @click="open('index.mikan')">index.mikan</el-button>
        <el-button :plain="true" @click="open('plus')">plus</el-button>
        <el-button :plain="true" @click="open('sea')">sea</el-button>
        <el-button :plain="true" @click="open('test')">
          <img src="~/static/img/test.png">
          <p>test</p>
        </el-button>
      </el-row>
      <el-table
        :data="tableData"
        style="width: 100%">
        <el-table-column
          prop="date"
          label="Date"
          width="180">
        </el-table-column>
        <el-table-column
          prop="name"
          label="Name"
          width="180">
        </el-table-column>
        <el-table-column
          prop="address"
          label="Address">
          <template slot-scope="scope">
            <el-button type="primary" @click="play(scope.row.url)" v-if="scope.row.url">
              <i class="el-icon-caret-right"></i>
            </el-button>
            <el-button disabled v-else><i class="el-icon-close"></i></el-button>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
import Vue from 'vue'
export default {
  data() {
    return {
      tableData: [{
        date: '2016-05-03',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-04',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles',
        url: 'https://s3-ap-northeast-1.amazonaws.com/gashapon-demo/static/96007906.m4a'
      }, {
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }]
    }
  },
  methods: {
    open(name) {
      this.$router.push(name)
    },
    play(url) {
      console.log(url)
      const audioElem = new Audio()
      audioElem.src = url
      audioElem.play()
    }
  }
}
</script>

<style scoped>
.video {
  position: relative;
  width: 100%;
  padding-top: 56.25%;
}
.video iframe {
  position: absolute;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
}

div.el-row {
  margin: 0.5rem 0;
}
</style>
