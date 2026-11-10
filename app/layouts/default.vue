<script setup lang="ts">
import type { ContentNavigationItem } from "@nuxt/content";
import { Acknowledgement, IDCFooter, IDCHeader, ScrollToTopButton } from "@idn-au/idn-lib";
import { getNavigation } from "~/utils/helpers";

const route = useRoute();

const { data: navigation } = await useAsyncData("navigation-merged", () => getNavigation(true), {
    default: () => [] as ContentNavigationItem[],
});
</script>

<template>
    <div class="flex flex-col min-h-dvh">
        <IDCHeader :navigation="navigation" :external="false" baseUrl="/" />
        <main class="grow mb-12">
            <LandingPageVideo v-if="route.path === '/'" />
            <slot />
        </main>
        <Acknowledgement />
        <IDCFooter :navigation="navigation" :external="false" />
        <ScrollToTopButton />
    </div>
</template>

<style scoped>

</style>
