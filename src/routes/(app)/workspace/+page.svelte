<script lang="ts">
	import { goto } from '$app/navigation';
	import { user } from '$lib/stores';
	import { onMount } from 'svelte';

	onMount(() => {
		if ($user?.role !== 'admin') {
			if ($user?.permissions?.workspace?.models) {
				goto('/assistant/workspace/models');
			} else if ($user?.permissions?.workspace?.knowledge) {
				goto('/assistant/workspace/knowledge');
			} else if ($user?.permissions?.workspace?.prompts) {
				goto('/assistant/workspace/prompts');
			} else if ($user?.permissions?.workspace?.tools) {
				goto('/assistant/workspace/tools');
			} else {
				goto('/assistant/');
			}
		} else {
			goto('/assistant/workspace/models');
		}
	});
</script>
