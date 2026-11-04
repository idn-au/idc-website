<script setup lang="ts">
import { CardContent, ShadCard } from "~/components/ui/card";

const props = defineProps<VideoItem>();
</script>

<template>
    <Dialog>
        <DialogTrigger asChild>
            <div class="p-0.5 rounded-2xl cursor-pointer m-3 hover:m-0 transition-[margin]">
                <ShadCard class="h-full">
                    <CardContent class="">
                        <EmbedVideo :url="props.url" class="pointer-events-none w-full" />
                        <h5 class="text-lg leading-snug">
                            {{ props.title }}
                        </h5>
                        <div v-if="props.description">
                            <p>{{ props.description }}</p>
                        </div>
                    </CardContent>
                </ShadCard>
            </div>
        </DialogTrigger>
        <DialogContent class="sm:max-w-5xl">
            <DialogHeader>
                <h3 class="font-bold my-0">{{ props.title }}</h3>
            </DialogHeader>
            <div v-if="props.description">
                <p>{{ props.description }}</p>
            </div>
            <div class="">
                <EmbedVideo :url="props.url" class="mx-auto w-full max-w-4xl" />
            </div>
        </DialogContent>
    </Dialog>
</template>

<style scoped>

</style>
