<script setup>
import { ref } from "vue";
import LayoutTop from "@/components/LayoutComponents/LayoutTop.vue";
import LayoutMenu from "@/components/LayoutComponents/LayoutMenu.vue";
import {Timer} from "@element-plus/icons-vue";
const value = ref()
//用来填充的文字
const content = ref('Nowadays, some universities in China ' +
    'has been forbidden to use product by MATHWORK, e.g. Matlab.' +
    ' Many professors and students were complaining about the decision ' +
    'because they use Matlab daily for their research and homework. Well, ' +
    'although we have alternative programming choice like C++ and python, ' +
    'Matlab do really has its own irreplacable good characteristics in computation ' +
    'and simulation. Under this circumstance, Julia was developed as an open source,' +
    ' free computation language to replace Matlab. Users can easily use it with ' +
    'different IDE like vscode and ATOM. In this article, we want to introduce' +
    ' some basic usage of it and compare the performance with different languages.'
)
const active = ref('1')
</script>

<template>
  <div class="w-screen h-screen relative block overflow-x-hidden bg-white">
    <!-- 顶部导航栏 -->
    <LayoutTop />
    <!-- 顶部标题栏 -->
    <div class="w-2/3 h-[100px] mt-20 relative block mx-auto overflow-hidden">
      <div class="w-full h-10 leading-10 relative block text-[30px] font-bold text-black text-center">
        新闻中心
      </div>
      <div style="height: calc(100%- 52px)" class="w-full relative flex">
        <LayoutMenu />
      </div>
      <el-divider style="margin-top: 5px;margin-bottom: 5px" direction="horizontal" />
    </div>
    <!-- 新闻页面 -->
    <div style="height: calc(100% - 100px)" class="w-2/3 none-scroll mx-auto grid overflow-y-scroll grid-cols-3 gap-3 relative">
      <div class="col-span-2 h-full relative block">
        <el-card
            class="w-full h-auto mb-4 relative block"
            v-for="item in 4"
            :key="item"
        >
          <template #header>
            <span class="hover:text-[#409EFF] cursor-pointer">Comparison Between Matlab and Julia</span>
          </template>
          <div class="w-full h-auto pb-4 relative whitespace-pre-line leading-4 text-ellipsis block overflow-hidden">
            {{content}}
          </div>
          <el-collapse>
            <el-collapse-item title="评论">
              <div class="w-full h-[300px] relative block bg-red-950">

              </div>
            </el-collapse-item>
          </el-collapse>
          <template #footer>
            <span>
              <el-icon><Timer /></el-icon>
              2024-04-14
            </span>
          </template>
        </el-card>
      </div>
      <!-- 右侧工具栏 -->
      <div class="w-full h-full relative block">
        <!-- 搜索栏 -->
        <el-card
            class="w-full h-[150px] mb-4 relative block"
        >
          <template #header>
            <span>搜索</span>
          </template>
          <div class="w-full h-[50px] relative flex">
            <el-input v-model="value" placeholder="搜索" clearable class="my-auto" />
            <el-button type="primary" class="my-auto ml-4" icon="Search">搜索</el-button>
          </div>
        </el-card>
        <!-- 最近投稿 -->
        <el-card
            class="w-full h-auto mb-4 relative block"
        >
          <template #header>
            <span>最近投稿</span>
          </template>
          <el-collapse v-model="active" accordion>
            <el-collapse-item title="2024-04" name="1">
              <div class="w-full h-auto relative block">
                <p v-for="item in 2" :key="item" class="mb-4 leading-4 text-black text-center hover:text-[#409EFF] cursor-pointer">Comparison Between Matlab and Julia</p>
              </div>
            </el-collapse-item>
            <el-collapse-item title="2024-03" name="2">
              <div class="w-full h-[100px] relative block bg-red-950"></div>
            </el-collapse-item>
          </el-collapse>
        </el-card>
      </div>
    </div>
    <!-- 分页组件 -->
    <div class="w-2/3 h-auto relative flex justify-center mx-auto">
      <el-pagination layout="prev, pager, next" :total="50" />
    </div>
  </div>
</template>

<style scoped>
@import "../../assets/temp.css";
</style>