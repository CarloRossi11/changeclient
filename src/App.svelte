<script>
	import Header from './components/Header.svelte'
	import Footer from './components/Footer.svelte'
	import PollList from './components/PollList.svelte'
	import CreateOppForm from './components/CreateOppForm.svelte'
	import Tabs from './shared/Tabs.svelte'
	import OppFetch from './components/OppFetch.svelte';
	import About from './components/About.svelte'

	//tabs
	let items = ['Current Opportunities', 'Add New Opportunity', 'About']
	let activeItem = 'Current Opportunities'
	const tabChange = (e) => {
	  activeItem = e.detail
	}

	//polls
	const handleAdd = (e) => {
	  activeItem = 'Current Opportunities'
	}
</script>

<Header/>
<main>
	<Tabs {activeItem} {items} on:tabChange={tabChange}/>
	{#if activeItem === 'Current Opportunities'}
		<OppFetch />
		<!-- <PollList /> -->
	{:else if activeItem === 'About'}
		<About/>
	{:else if activeItem === 'Add New Opportunity'}
		<CreateOppForm on:add={handleAdd}/>
	{/if}
</main>
<Footer/>

<style>
	main{
		max-width: 960px;
		margin: 40px auto;
	}
</style>

