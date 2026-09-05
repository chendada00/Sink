<script setup lang="ts">
import type { NuxtError } from '#app'
import { ArrowLeft, LayoutDashboard, TriangleAlert } from '@lucide/vue'

defineProps<{
  error: NuxtError
}>()
</script>

<template>
  <NuxtLayout name="home">
    <section class="relative flex flex-1 items-center justify-center overflow-hidden px-6 py-20">
      <div class="absolute -top-24 right-0 size-80 rounded-full bg-muted blur-3xl" />

      <div class="relative w-full max-w-lg text-center">
        <div class="mx-auto flex size-12 items-center justify-center rounded-xl border bg-card text-muted-foreground">
          <TriangleAlert class="size-5" />
        </div>

        <p class="mt-8 text-sm font-medium text-muted-foreground">
          {{ error.statusCode || 404 }}
        </p>
        <h1 class="mt-2 text-3xl font-semibold tracking-tight">页面没有找到</h1>
        <p class="mt-4 leading-7 text-muted-foreground">
          这个链接可能已失效、被修改，或从未存在过。
        </p>

        <div class="mt-8 flex flex-col justify-center gap-3 sm:flex-row">
          <Button as-child>
            <NuxtLink to="/">
              <ArrowLeft class="size-4" />
              返回首页
            </NuxtLink>
          </Button>

          <Button as-child variant="outline">
            <NuxtLink to="/dashboard">
              <LayoutDashboard class="size-4" />
              进入管理后台
            </NuxtLink>
          </Button>
        </div>
      </div>
    </section>
  </NuxtLayout>
</template>