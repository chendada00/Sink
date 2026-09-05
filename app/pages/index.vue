<script setup lang="ts">
import {
  Activity,
  ArrowRight,
  BarChart3,
  Link2,
  ShieldCheck,
} from '@lucide/vue'

definePageMeta({ layout: 'home' })

const features = [
  { icon: Link2, title: '简洁短链', text: '让分享地址保持清晰、易记。' },
  { icon: BarChart3, title: '访问分析', text: '了解链接的访问趋势与来源。' },
  { icon: ShieldCheck, title: '自主掌控', text: '链接、数据与规则都由你管理。' },
]
</script>

<template>
  <section class="relative flex w-full overflow-hidden">
    <div class="home-orb absolute -top-32 -left-24 size-96 rounded-full bg-primary/10 blur-3xl" />
    <div class="home-orb-delayed absolute right-0 bottom-0 size-80 rounded-full bg-muted blur-3xl" />

    <div class="relative mx-auto flex w-full max-w-5xl flex-col justify-center px-6 py-20 md:py-28">
      <div class="grid items-center gap-14 lg:grid-cols-[1.15fr_0.85fr]">
        <div class="home-enter">
          <div class="mb-6 inline-flex items-center gap-2 rounded-full border bg-card px-3 py-1.5 text-sm text-muted-foreground">
            <span class="size-2 rounded-full bg-success" />
            你的专属短链接空间
          </div>

          <h1 class="max-w-2xl text-4xl font-semibold tracking-tight text-balance md:text-6xl">
            让每一条链接，
            <span class="text-muted-foreground">都有清晰的去处。</span>
          </h1>

          <p class="mt-6 max-w-xl text-lg leading-8 text-muted-foreground">
            一个安静、可靠的链接管理入口。创建短链，查看访问数据，把分享保持在自己的掌控中。
          </p>

          <div class="mt-9 flex flex-col gap-3 sm:flex-row">
            <Button as-child size="lg">
              <NuxtLink to="/dashboard">
                打开管理后台
                <ArrowRight class="size-4" />
              </NuxtLink>
            </Button>
            <Button as-child size="lg" variant="outline">
              <a href="#features">了解功能</a>
            </Button>
          </div>
        </div>

        <div class="home-panel rounded-xl border bg-card p-5 shadow-sm">
          <div class="flex items-center justify-between border-b pb-4">
            <div>
              <p class="text-sm font-medium">链接状态</p>
              <p class="mt-1 text-xs text-muted-foreground">实时同步到你的仪表盘</p>
            </div>
            <Activity class="size-5 text-success" />
          </div>

          <div class="mt-6 rounded-lg bg-muted p-4">
            <p class="text-xs text-muted-foreground">短链接</p>
            <div class="mt-2 flex items-center justify-between gap-3">
              <span class="truncate font-mono text-sm">你的域名 / welcome</span>
              <span class="shrink-0 rounded-full bg-success/15 px-2 py-1 text-xs font-medium text-success">
                已启用
              </span>
            </div>
          </div>

          <div class="mt-4 grid grid-cols-3 gap-3">
            <div v-for="label in ['访问记录', '来源统计', '实时事件']" :key="label" class="rounded-lg border p-3">
              <div class="mb-3 h-1.5 w-8 rounded-full bg-primary/20" />
              <p class="text-xs text-muted-foreground">{{ label }}</p>
            </div>
          </div>
        </div>
      </div>

      <div id="features" class="mt-20 grid gap-4 md:grid-cols-3">
        <article v-for="feature in features" :key="feature.title" class="rounded-xl border bg-card p-5 transition-transform duration-300 hover:-translate-y-1">
          <component :is="feature.icon" class="size-5 text-muted-foreground" />
          <h2 class="mt-5 font-medium">{{ feature.title }}</h2>
          <p class="mt-2 text-sm leading-6 text-muted-foreground">{{ feature.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.home-enter {
  animation: enter 700ms ease-out both;
}

.home-panel {
  animation: enter 700ms 120ms ease-out both;
}

.home-orb {
  animation: drift 12s ease-in-out infinite;
}

.home-orb-delayed {
  animation: drift 14s -5s ease-in-out infinite reverse;
}

@keyframes enter {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes drift {
  50% { transform: translate3d(20px, 28px, 0) scale(1.08); }
}

@media (prefers-reduced-motion: reduce) {
  .home-enter,
  .home-panel,
  .home-orb,
  .home-orb-delayed {
    animation: none;
  }
}
</style>