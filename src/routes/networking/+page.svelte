<script>
    import { Wifi, Server, ArrowRight } from 'lucide-svelte';

    const categories = [
        {
            name: 'IP Addressing',
            items: [
                { name: 'IP Address', url: '/networking/ipaddress' },
                { name: 'Subnet', url: '/networking/subnet' },
                { name: 'MAC Address', url: '/networking/mac-address' },
                { name: 'ARP', url: '/networking/arp' }
            ]
        },
        {
            name: 'Protocols and Models',
            items: [
                { name: 'OSI Model', url: '/networking/osi-model' },
                { name: 'TCP and UDP', url: '/networking/tcp-udp' }
            ]
        },
        {
            name: 'Network Services',
            items: [
                { name: 'DHCP', url: '/networking/dhcp' },
                { name: 'DNS', url: '/networking/dns' },
                { name: 'DNS Records', url: '/networking/dns-records' }
            ]
        },
        {
            name: 'Network Configuration',
            items: [
                { name: 'VLAN', url: '/networking/vlan' },
                { name: 'NAT', url: '/networking/nat' },
                { name: 'Network Ports', url: '/networking/networkports' }
            ]
        }
    ];
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
    <div class="container mx-auto px-4 py-8 max-w-4xl">
        <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-2">
            <Wifi class="text-blue-400" size={36} />
            Networking
        </h1>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            {#each categories as category}
                <div class="bg-gray-800 p-6 rounded-lg shadow-lg hover:shadow-xl transition">
                    <h2 class="text-2xl font-semibold text-blue-500 mb-4">{category.name}</h2>
                    <ul class="space-y-2">
                        {#each category.items as item}
                            <li>
                                <a href={item.url} class="flex items-center justify-between text-blue-400 hover:text-blue-300 transition-colors">
                                    <span>{item.name}</span>
                                    <ArrowRight class="text-blue-400" size={16} />
                                </a>
                            </li>
                        {/each}
                    </ul>
                </div>
            {/each}
        </div>
    </div>
</div>