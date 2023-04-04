<template>
    <nav>
        <router-link to="/">home</router-link>
        <router-link to="more">more</router-link>
    </nav>

    <!-- 只有 include 的组件才会被 keep-alive，名字为组件的 name 属性定义 -->
    <!-- key 可以使 user/1 user/2，不会复用组件。user?id=1 user?id=2 也不会 -->
    <!-- 值改为 $route.path，则 user? 这种方式会复用组件 -->
    <!-- router-view vue3 写法变复杂了 -->
    <router-view v-slot="{ Component }">
        <keep-alive :include="['home', 'more']">
            <component :is="Component" :key="$route.fullPath" />
        </keep-alive>
    </router-view>
</template>