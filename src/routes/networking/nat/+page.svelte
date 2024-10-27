<script>
  import { ChevronDown, ChevronUp, Network, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; // trigger reactivity
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-yellow-400 mb-8 flex items-center gap-3">
      <Network class="text-yellow-400" size={36} />
      Mastering Network Address Translation (NAT)
    </h1>

    <!-- Introduction to NAT Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What is NAT?</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            NAT, or Network Address Translation, is the lifebuoy keeping IPv4 alive and kicking. It lets us use a single public IP address for multiple devices' private IPs, conserving our precious supply of IPv4 addresses in a world where everyone needs internet access.
          </p>

          <div class="bg-yellow-900/50 border border-yellow-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-yellow-400" size={20} />
              <h3 class="text-lg font-semibold text-yellow-300">TLDR</h3>
            </div>
            <p class="text-yellow-100">
              NAT translates private IPs to a public IP, allowing multiple devices to share a single internet connection.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Functionality of NAT Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('functionality')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How NAT Works</h2>
        </div>
        <svelte:component this={expandedSections['functionality'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['functionality']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            NAT performs a magical juggling act, converting private IP addresses from your home or business network into a single public IP address for internet access and vice versa. It's efficient, cost-effective, and saves the internet from running out of addresses!
          </p>

          <div class="bg-yellow-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-yellow-300 mb-2">Process:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Devices inside a network have private IPs.</li>
              <li>Router assigns these devices private IP addresses.</li>
              <li>NAT translates these private addresses to a public IP for internet access.</li>
              <li>Incoming traffic converts public IPs back to private IPs using NAT.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Types of IP Addresses Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('ipTypes')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Public vs. Private IPs</h2>
        </div>
        <svelte:component this={expandedSections['ipTypes'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['ipTypes']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Public IP addresses are registered and necessary to access the internet, whereas private IPs are used within local networks. NAT translates between these to conserve public IP usage and allow seamless device connectivity.
          </p>

          <div class="bg-yellow-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-yellow-300 mb-2">Differences:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li><strong>Public IPs:</strong> Limited and registered for internet access.</li>
              <li><strong>Private IPs:</strong> Unlimited and used within local networks.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Future of IP Networking Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('future')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The Future with IPv6</h2>
        </div>
        <svelte:component this={expandedSections['future'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['future']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            The days of NAT are numbered with the rise of IPv6, which boasts over 340 undecillion addresses—enough for every device on the planet to have a public IP. This update will eventually eliminate the need for private IPs and translation.
          </p>

          <div class="bg-yellow-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-yellow-300 mb-2">IPv6 Features:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>340 undecillion IP addresses—a mind-bending number!</li>
              <li>Eliminates the need for NAT, allowing direct device communication.</li>
              <li>Simplifies network operations with more efficient routing.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>