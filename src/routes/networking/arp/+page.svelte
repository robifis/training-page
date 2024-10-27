<script>
  import { ChevronDown, ChevronUp, Link2, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; // trigger reactivity
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-green-400 mb-8 flex items-center gap-3">
      <Link2 class="text-green-400" size={36} />
      Cracking the ARP Code
    </h1>

    <!-- Introduction to ARP Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What is ARP?</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            ARP—Address Resolution Protocol—is the bridge that binds IP addresses to MAC addresses. It allows devices to find and connect with each other on a local network by acquiring the necessary MAC address for communication.
          </p>

          <div class="bg-green-900/50 border border-green-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-green-400" size={20} />
              <h3 class="text-lg font-semibold text-green-300">TLDR</h3>
            </div>
            <p class="text-green-100">
              ARP matches IP addresses to MAC addresses to enable network devices to communicate on local networks.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- How ARP Works Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('howItWorks')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How ARP Works</h2>
        </div>
        <svelte:component this={expandedSections['howItWorks'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['howItWorks']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            When a device knows the IP address but needs the MAC address, it sends an ARP broadcast asking for the MAC. The device with the matching IP responds, and the requester stores this in its ARP cache to speed up future requests.
          </p>

          <div class="bg-green-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-green-300 mb-2">Steps Involved:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Device A looks in its ARP cache for Device B's MAC.</li>
              <li>If it's not there, Device A broadcasts an ARP request.</li>
              <li>Device B responds with its MAC address.</li>
              <li>Device A stores this info in its ARP cache for future use.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Types of ARP Entries Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('arpEntries')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Types of ARP Entries</h2>
        </div>
        <svelte:component this={expandedSections['arpEntries'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['arpEntries']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            ARP entries can be dynamic or static. Dynamic entries are created automatically and periodically refreshed, whereas static entries are manually set and stay for as long as the system is up or until they’re removed.
          </p>

          <div class="bg-green-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-green-300 mb-2">Entry Types:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li><strong>Dynamic:</strong> Created automatically through ARP requests and time out automatically.</li>
              <li><strong>Static:</strong> Manually configured using 'arp -s' and remain until manually removed.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Managing ARP Entries Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('manageArp')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Managing ARP Entries</h2>
        </div>
        <svelte:component this={expandedSections['manageArp'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['manageArp']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            You can view and manage the ARP cache using command-line tools. Check it out with 'arp -a' to see current entries or use 'arp -s' to configure static entries.
          </p>

          <div class="bg-green-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-green-300 mb-2">Commands and Usage:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li><code>arp -a</code>: View current ARP entries in the cache.</li>
              <li><code>arp -s IP MAC</code>: Add a static ARP entry.</li>
              <li>Static entries minimize ARP broadcast traffic—ideal for known device interactions.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>