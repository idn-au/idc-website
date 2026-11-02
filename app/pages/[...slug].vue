<script lang="ts" setup>
import { IDCPageHeader } from "@idn-au/idn-lib";
import { File } from "@lucide/vue";

const route = useRoute();

const { data: page } = await useAsyncData(route.path, () => {
    if (route.path.split("/").some(s => s.startsWith("_"))) {
        return undefined;
    }
    else {
        return queryCollection("content")
            .path(route.path)
            .first();
    }
});

useHead({
    titleTemplate: (titleChunk) => {
        let title = "The Indigenous Data Commons";
        if (page.value) {
            if (page.value.path !== "/") {
                title = `${page.value.title} | ${title}`;
            }
        }
        else {
            title = `Not found | ${title}`;
        }
        return title;
    },
});
</script>

<template>
    <div v-if="page" class="prose dark:prose-invert max-w-[unset]">
        <IDCPageHeader v-if="route.path !== '/'" :image="page.image">
            <template #title>
                {{ page.title }}
            </template>
            <template #description>
                {{ page.description }}
            </template>
        </IDCPageHeader>
        <div class="mx-auto max-w-[1200px] px-2">
            <Breadcrumbs v-if="route.path !== '/'" />
            <ContentRenderer v-if="page?.body?.value.length > 0" :value="page" />
            <Empty v-else class="">
                <EmptyHeader>
                    <EmptyMedia variant="icon">
                        <File />
                    </EmptyMedia>
                    <EmptyTitle>Content coming soon</EmptyTitle>
                    <EmptyDescription>This page is currently under construction. Check back soon.</EmptyDescription>
                </EmptyHeader>
            </Empty>
        </div>
    </div>
    <div v-else>
        <h1>Page not found</h1>
        <p>
            Sorry, this page does not exist. <NuxtLink to="/">
                Go home
            </NuxtLink>.
        </p>
    </div>
</template>
