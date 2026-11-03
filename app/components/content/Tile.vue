<script lang="ts" setup>
import type { HTMLAttributes } from "vue";
import { IDCLink } from "@idn-au/idn-lib";
import { cn } from "~/lib/utils";

const props = defineProps<{
    to: string;
    img?: string;
    class?: HTMLAttributes["class"];
}>();
</script>

<template>
    <div class="flex items-center justify-center">
        <IDCLink
            :to="props.to"
            :external="false"
            :class="cn('aspect-square flex items-center justify-center border rounded-4xl p-4 dark bg-secondary hover:no-underline! hover:scale-110 transition-transform w-full', props.class)"
            :style="{ background: `linear-gradient(transparent, var(--isu-black)), url('${props.img}'), var(--isu-black)` }"
        >
            <div class="text-white! text-center text-base md:text-2xl font-bold">
                <slot mdcUnwrap="p" />
            </div>
        </IDCLink>
    </div>
</template>
