<template>
  <PageWrapper title="卡片列表示例" content="基础封装">
    <CardList
      :params="params"
      :api="demoListApi"
      @getMethod="getMethod"
      @delete="handleDel"
    >
      <template #header>
        <Button type="primary" color="error"> 按钮1 </Button>
        <Button type="primary" color="success"> 按钮2 </Button>
      </template>
    </CardList>
  </PageWrapper>
</template>
<script lang="ts" setup>
import { Button } from 'ant-design-vue'
import { CardList } from '@/components/card-list'
import { PageWrapper } from '@/components/page'
import { demoListApi } from '@pkg/apis/demo'
import { useMessage } from '@/hooks/web/useMessage'
const { notification } = useMessage()
// 请求api时附带参数
const params = {}

let reload = () => {}
// 获取内部fetch方法;
function getMethod(m: any) {
  reload = m
}
//删除按钮事件
function handleDel(id) {
  console.log(id)
  notification.success({ message: `成功删除${id}` })
  reload()
}
</script>
