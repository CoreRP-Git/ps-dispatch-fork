<script lang="ts">
	import VisibilityProvider from '@providers/VisibilityProvider.svelte'
	import { BROWSER_MODE, RESOURCE_NAME, VISIBILITY, Locale  } from '@store/stores'
	import DebugBrowser from '@providers/DebugBrowser.svelte'
	import AlwaysListener from '@providers/AlwaysListener.svelte'
	import Menu from '@components/Menu.svelte'
	import Main from '@components/Main.svelte'

	$RESOURCE_NAME  = 'ps-dispatch'

	const isEnvBrowser = () => {
		return typeof window !== 'undefined';
	}

	let backgroundStyle = '';

	if (isEnvBrowser()) {
		backgroundStyle = `
			background-image: url("https://i.imgur.com/3pzRj9n.png");
			background-size: cover;
			background-repeat: no-repeat;
			background-position: center;
		`;
	}
</script>

{#if $Locale}
	<VisibilityProvider>
		<Menu />
	</VisibilityProvider>

	<Main />
{/if}

<AlwaysListener />

{#if $BROWSER_MODE}
	<DebugBrowser />
{/if}


<div style={backgroundStyle} class="absolute inset-0 -z-10"></div>
