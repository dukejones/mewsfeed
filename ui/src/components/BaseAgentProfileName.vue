<template>
  <div>
    <div v-if="profile" class="flex space-x-2">
      <div
        v-if="profile.fields[PROFILE_FIELDS.DISPLAY_NAME]"
        class="text-primary font-bold"
      >
        {{ profile.fields[PROFILE_FIELDS.DISPLAY_NAME] }}
      </div>
      <div class="font-mono">@{{ profile.nickname }}</div>
    </div>
    <div v-else class="font-mono">
      {{ encodeHashToBase64(agentPubKey).slice(0, 8) }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { Profile } from "@holochain-open-dev/profiles";
import { PROFILE_FIELDS } from "@/types/types";
import { AgentPubKey, encodeHashToBase64 } from "@holochain/client";

defineProps<{
  profile?: Profile | null;
  agentPubKey: AgentPubKey;
}>();
</script>

<style scoped></style>
