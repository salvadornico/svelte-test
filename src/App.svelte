<script>
	import Navbar from "./Navbar.svelte"
	import Player from "./Player.svelte"
	import AddPlayer from "./AddPlayer.svelte"

	let players = [
		{ name: "Lionel Messi", points: 50 },
		{ name: "Luis Suarez", points: 40 },
		{ name: "Ousmane Dembele", points: 20 },
	]

	const addPlayer = e => {
		const newPlayer = e.detail

		players = [ ...players, newPlayer ]
	}

	const deletePlayer = e => {
		const { name, points } = e.detail

		players = players.filter(player => player.name != name && player.points != points)
	}
</script>

<Navbar />
<div class="container">
	<AddPlayer on:addplayer={addPlayer} />

	{#if players.length === 0}
		<p>No players</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.points} on:deleteplayer={deletePlayer}/>
		{/each}
	{/if}
</div>
