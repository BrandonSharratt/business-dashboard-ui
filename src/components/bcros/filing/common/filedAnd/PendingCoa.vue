<template>
  <div class="flex flex-col gap-1 items-start w-full">
    <span>
      {{ $t('text.filing.filedAndPending') }}
      <BcrosFilingCommonFiledLabel :filing="filing" />
    </span>
    <BcrosTooltip
      :text="tooltipText"
      :popper="{
        placement: 'top',
        arrow: true
      }"
    >
      <UIcon class="text-orange-500" name="i-mdi-alert" />
    </BcrosTooltip>
  </div>
</template>

<script setup lang="ts">
import type { ApiResponseFilingI } from '~/interfaces/filing-i'

const t = useNuxtApp().$i18n.t

const props = defineProps({
  filing: { type: Object as PropType<ApiResponseFilingI>, required: true }
})

/** The effective date-time of this filing. */
const effectiveDateTime = computed((): string =>
  props.filing.effectiveDate
    ? dateToPacificDateTime(new Date(props.filing.effectiveDate))
    : '[unknown]'
)

const tooltipText = computed(() =>
  `${t('tooltip.pendingAddressChange').replace('COA_EFFECTIVE_DATE', effectiveDateTime.value)}`
)
</script>
