<script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>

<template>
  <div class="w-full h-screen">
    <div class="w-full h-full flex flex-col">
        <div class="w-full">
           <div class="w-2/4"><input class="input" type="text" id="" placeholder="請注意事項"></div>
            <button class="right">新增</button>
        </div>
        <div class="w-full flex">
            <button class="content content-1" data-search="all">全部</button>
            <button class="content content-2" data-search="isTodo">已執行</button>
            <button class="content content-3" data-search="notTodo">未執行</button>
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
