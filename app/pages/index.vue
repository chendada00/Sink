<script setup lang="ts">
import {
  ArrowRight,
  ArrowUpRight,
  BarChart3,
  Link2,
  ShieldCheck,
} from '@lucide/vue'

definePageMeta({ layout: 'home' })

const featuredLinks = [
  // 在这里填你想展示的 3–6 条短链：
  { title: '个人主页', description: '关于我与联系方式', href: '/home' },
  { title: '个人博客', description: '记录生活', href: '/blog' },
  { title: '个人导航', description: '个人常用网站收藏', href: '/nav' },
  { title: '个人图床', description: '图片收藏与分享', href: '/pic' },
]

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

    <div class="relative mx-auto w-full max-w-5xl px-6 py-20 md:py-28">
      <div class="grid items-center gap-14 lg:grid-cols-[1.15fr_0.85fr]">
        <div class="home-enter">
          <div class="mb-6 inline-flex rounded-full border bg-card px-3 py-1.5 text-sm text-muted-foreground">
            你的专属短链接空间
          </div>

          <h1 class="max-w-2xl text-4xl font-semibold tracking-tight md:text-6xl">
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
            <Button v-if="featuredLinks.length" as-child size="lg" variant="outline">
              <a href="#featured-links">常用链接</a>
            </Button>
          </div>
        </div>

        <div class="home-panel rounded-xl border bg-card p-5 shadow-sm">
          <p class="text-sm font-medium">链接管理</p>
          <p class="mt-1 text-sm text-muted-foreground">创建、管理并分析你的短链接。</p>

          <div class="mt-6 rounded-lg bg-muted p-4">
            <p class="text-xs text-muted-foreground">状态</p>
            <p class="mt-2 font-medium">服务运行正常</p>
          </div>
        </div>
      </div>

      <section v-if="featuredLinks.length" id="featured-links" class="mt-20">
        <p class="text-sm text-muted-foreground">精选</p>
        <h2 class="mt-1 text-2xl font-semibold">常用链接</h2>

        <div class="mt-6 grid gap-3 md:grid-cols-2 lg:grid-cols-3">
          <a
            v-for="link in featuredLinks"
            :key="link.href"
            :href="link.href"
            class="group rounded-xl border bg-card p-5 transition-transform duration-300 hover:-translate-y-1 hover:bg-accent"
          >
            <div class="flex items-start justify-between gap-3">
              <h3 class="font-medium">{{ link.title }}</h3>
              <ArrowUpRight class="size-4 text-muted-foreground" />
            </div>
            <p class="mt-2 text-sm leading-6 text-muted-foreground">
              {{ link.description }}
            </p>
          </a>
        </div>
      </section>

      <div class="mt-20 grid gap-4 md:grid-cols-3">
        <article
          v-for="feature in features"
          :key="feature.title"
          class="rounded-xl border bg-card p-5 transition-transform duration-300 hover:-translate-y-1"
        >
          <component :is="feature.icon" class="size-5 text-muted-foreground" />
          <h2 class="mt-5 font-medium">{{ feature.title }}</h2>
          <p class="mt-2 text-sm leading-6 text-muted-foreground">{{ feature.text }}</p>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.home-enter { animation: enter 700ms ease-out both; }
.home-panel { animation: enter 700ms 120ms ease-out both; }
.home-orb { animation: drift 12s ease-in-out infinite; }
.home-orb-delayed { animation: drift 14s -5s ease-in-out infinite reverse; }

@keyframes enter {
  from { opacity: 0; transform: translateY(16px); }
  to { opacity: 1; transform: translateY(0); }
}

@keyframes drift {
  50% { transform: translate3d(20px, 28px, 0) scale(1.08); }
}
</style>