<template>
    <nav class="navbar navbar-dark bg-primary justify-content-between mb-4 px-4">
        <router-link class="navbar-brand" to="/">专栏zh</router-link>
        <ul v-if="!props.user.isLogin" class="list-inline mb-0">
            <li class="list-inline-item">
                <router-link to="/login" class="btn btn-outline-light my-2">登陆</router-link>
            </li>
            <li class="list-inline-item">
                <router-link to="/signup" class="btn btn-outline-light my-2">注册</router-link>
            </li>
        </ul>
        <ul v-else class="list-inline mb-0">
            <li class="list-inline-item">
                <Dropdown :title="`你好 ${props.user.nickName}`">
                    <DropdownItem>
                        <router-link to="/create" class="dropdown-item">新建文章</router-link>
                    </DropdownItem>
                    <DropdownItem>
                        <router-link :to="`/column/${props.user.column}`" class="dropdown-item">我的专栏</router-link>
                    </DropdownItem>
                    <DropdownItem disabled><a href="#" class="dropdown-item">编辑资料</a></DropdownItem>
                    <DropdownItem><a href="#" class="dropdown-item">退出登陆</a></DropdownItem>
                </Dropdown>
            </li>
        </ul>
    </nav>
</template>

<script lang="ts" setup name="GlobalHeader">
import { defineProps, PropType } from 'vue'
import Dropdown from './Dropdown.vue'
import DropdownItem from './DropdownItem.vue'
import { UserProps } from '@/store'

const props = defineProps({
    user: {
        type: Object as PropType<UserProps>,
        required: true
    }
})
</script>
