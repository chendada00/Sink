<script setup lang="ts">
import { LayoutDashboard } from '@lucide/vue'

const { title } = useAppConfig()
</script>

<template>
  <div class="flex min-h-svh flex-col bg-background text-foreground">
    <header class="border-b">
      <div class="mx-auto flex max-w-5xl items-center justify-between px-6 py-4">
        <NuxtLink to="/" class="flex items-center gap-2 font-bold">
          <img src="/sink.png" :alt="title" class="size-8 rounded-full">
          <span>{{ title }}</span>
        </NuxtLink>

        <Button as-child size="sm">
          <NuxtLink to="/dashboard">
            <LayoutDashboard class="size-4" />
            进入管理后台
          </NuxtLink>
        </Button>
      </div>
    </header>

    <main class="flex flex-1">
      <slot />
    </main>

    <footer class="border-t">
      <div class="mx-auto flex max-w-5xl justify-between px-6 py-5 text-xs text-muted-foreground">
        <span>个人链接服务</span>
        <span>私有 · 可控 · 可追踪</span>
      </div>
    </footer>
  </div>
</template>