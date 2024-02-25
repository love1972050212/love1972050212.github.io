<script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <div class="w-full h-screen bg-indigo-500">
    <div class="w-1/2 m-auto h-full flex flex-col bg-white gap-4">
        <div class="w-full flex ml-1">
           <div class="w-2/4"><input class="input" type="text" id="" placeholder="請注意事項"></div>
            <button class="right bg-indigo-500">新增</button>
        </div>
        <div class="w-full flex gap-3 ml-1">
            <button class="bg-indigo-500 ..." data-search="all">全部</button>
            <button class="bg-indigo-500 ..." data-search="isTodo">已執行</button>
            <button class="bg-indigo-500 ..." data-search="notTodo">未執行</button>
        </div>
        <div class="w-full flex">
                <div class="flex-1">執行</div>
                <div class="flex-1">事項</div>
                <div class="flex-1">功能</div>
        </div>
        <div class="re">
        <div class="container2 data-show"></div>
        </div>
    </div>
  </div>
</template>
