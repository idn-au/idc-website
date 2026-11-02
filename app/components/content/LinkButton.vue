<script setup lang="ts">
import type { HTMLAttributes } from "vue";
import { IDCButton } from "@idn-au/idn-lib";
import { cn } from "~/lib/utils";

const props = defineProps<{
    to?: string;
    newTab?: boolean;
    variant?: InstanceType<typeof IDCButton>["$props"]["variant"];
    colour?: InstanceType<typeof IDCButton>["$props"]["colour"];
    size?: InstanceType<typeof IDCButton>["$props"]["size"];
    icon?: InstanceType<typeof IDCButton>["$props"]["icon"];
    class?: HTMLAttributes["class"];
}>();
</script>

<template>
    <IDCButton :variant="props.variant" :colour="props.colour" :icon="props.icon" :size="props.size" :class="cn('btn', props.class)" :asChild="!!props.to">
        <template v-if="props.to">
            <NuxtLink v-if="props.to.startsWith('/')" :to="props.to" :target="props.newTab ? '_blank' : undefined">
                <slot mdcUnwrap="p" />
            </NuxtLink>
            <a v-else :href="props.to" :target="props.newTab ? '_blank' : undefined" rel="noopener noreferrer">
                <slot mdcUnwrap="p" />
            </a>
        </template>
        <slot v-else mdcUnwrap="p" />
    </IDCButton>
</template>
