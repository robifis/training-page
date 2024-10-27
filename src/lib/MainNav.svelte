<script>
const submenu = [
		{
			name: 'Networking Fundamentals',
			submenu: [
				{
					name: 'IP Addressing',
					items: [
						{ name: 'IP Address', url: '/networking/ipaddress' },
						{ name: 'Subnet', url: '/networking/subnet' },
						{ name: 'MAC Address', url: '/networking/mac-address' },
						{ name: 'ARP', url: '/networking/arp' },
					]
				},
				{
					name: 'Protocols and Models',
					items: [
						{ name: 'OSI Model', url: '/networking/osi-model' },
						{ name: 'TCP and UDP', url: '/networking/tcp-udp' },
					]
				},
				{
					name: 'Network Services',
					items: [
						{ name: 'DHCP', url: '/networking/dhcp' },
						{ name: 'DNS', url: '/networking/dns' },
						{ name: 'DNS Records', url: '/networking/dns-records' },
					]
				},
				{
					name: 'Network Configuration',
					items: [
						{ name: 'VLAN', url: '/networking/vlan' },
						{ name: 'NAT', url: '/networking/nat' },
						{ name: 'Network Ports', url: '/networking/networkports' },
					]
				},
			],
		}
	];
</script>
<nav>
	<a href="/">Home</a>
	<div class="menu-item">
		<a href="/networking">Networking</a>
		<div class="submenu">
			<ul class="list-none">
				{#each submenu as category}
					<li class="decoration-none">
						<strong>{category.name}</strong>
						<ul>
							{#each category.submenu as subcategory}
								<li class="decoration-none">
									<em>{subcategory.name}</em>
									<ul>
										{#each subcategory.items as item}
											<li class="decoration-none">
												<a href={item.url}>{item.name}</a>
											</li>
										{/each}
									</ul>
								</li>
							{/each}
						</ul>
					</li>
				{/each}
			</ul>
		</div>
	</div>
</nav>
<style>
	nav {
		@apply flex justify-center gap-4 bg-gray-100 p-4 dark:bg-gray-800;
	}
	a {
		@apply w-max text-blue-500 dark:text-blue-300;
	}
	a:hover {
		@apply text-white underline;
	}
	.submenu {
		@apply absolute hidden border border-gray-300 bg-gray-100 p-2 dark:border-gray-700 dark:bg-gray-800;
	}
	.menu-item:hover .submenu {
		@apply block w-max;
	}
	.menu-item {
		@apply relative;
	}
</style>
