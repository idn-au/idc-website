<script setup lang="ts">
import { CardContent, ShadCard } from "~/components/ui/card";

const props = defineProps<{
    score: ScoreType;
}>();
</script>

<template>
    <ShadCard class="p-0">
        <CardContent class="p-0">
            <ScoreAccordion :scores="scoreDefs[props.score]" />
        </CardContent>
    </ShadCard>
</template>
