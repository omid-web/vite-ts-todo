<template lang="pug">
router-view
</template>

<script lang="ts" setup>
import authStore from '@store/auth';

const auth = authStore();

const router = useRouter();

const { logged } = toRefs(auth);

const checkAuth = (authValue: boolean) => {
  if (!authValue) {
    router.push({ name: 'sign-in' });
  }
};

checkAuth(logged.value);

watch(logged, () => {
  checkAuth(logged.value);
});
</script>

<script lang="ts">
export default {
  name: 'authenticated-layout',
};
</script>
