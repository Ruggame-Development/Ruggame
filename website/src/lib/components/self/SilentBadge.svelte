<script lang="ts">
	import * as Tooltip from '$lib/components/ui/tooltip';

	interface Props {
		icon: any;
		text: string;
		class?: string;
	}

	let { icon: Icon, text, class: className }: Props = $props();
</script>

<Tooltip.Root>
	<Tooltip.Trigger>
		<div class="cursor-pointer rounded-full p-1 opacity-80 hover:opacity-100 {className}">
			<Icon class="h-4 w-4" />
		</div>
	</Tooltip.Trigger>
	<Tooltip.Content
		class="bg-secondary text-secondary-foreground ring-border ring-1"
		arrowClasses="bg-secondary"
	>
		<p>{text}</p>
	</Tooltip.Content>
</Tooltip.Root>
