<script>
  import { ChevronDown, ChevronUp, Radio, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; // trigger reactivity
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-purple-400 mb-8 flex items-center gap-3">
      <Radio class="text-purple-400" size={36} />
      Unraveling MAC Addresses
    </h1>

    <!-- Introduction to MAC Address Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What is a MAC Address?</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            A MAC address is like a passport for your device, uniquely identifying every network device on the planet! It's a 6-byte, hex-coded identifier burned into the NIC by the manufacturer, which means no two devices share the same MAC address.
          </p>

          <div class="bg-purple-900/50 border border-purple-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-purple-400" size={20} />
              <h3 class="text-lg font-semibold text-purple-300">TLDR</h3>
            </div>
            <p class="text-purple-100">
              MAC addresses are unique addresses that identify network devices anywhere. They’re vital for device communication.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Purpose and Functionality Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('functionality')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Purpose and Functionality</h2>
        </div>
        <svelte:component this={expandedSections['functionality'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['functionality']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            MAC addresses ensure devices can talk to each other on the network. They're crucial whether devices are side-by-side or continents apart. While IP addresses are like the physical address of a house, MAC addresses are akin to the names of the residents. They're constant, unlike IP addresses, which can change.
          </p>

          <div class="bg-purple-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-purple-300 mb-2">Takeaways:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Unique and unchanging, MAC addresses identify devices on any network.</li>
              <li>Work alongside IP addresses for network communications.</li>
              <li>Utilized in ARP broadcasts for device identification and data transmission.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- How MAC Addresses Work Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('work')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How MAC Addresses Work</h2>
        </div>
        <svelte:component this={expandedSections['work'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['work']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            On a local network, devices find each other's MAC addresses using ARP broadcasts, allowing seamless communication. If a device needs to communicate with another on a different network, it relies on the network's routers to forward the data using MAC addresses at each step.
          </p>

          <div class="bg-purple-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-purple-300 mb-2">Steps Involved:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Device sends ARP request on the local network for the target device's MAC address.</li>
              <li>If devices are on different networks, routers pass data along, using MAC addresses successively.</li>
              <li>Data reaches the destination with each entity using MAC addresses at every hop.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Finding Your Device's MAC Address Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('findMac')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Finding Your Device's MAC Address</h2>
        </div>
        <svelte:component this={expandedSections['findMac'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['findMac']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Want to uncover your MAC address? On a Windows device, hit the command prompt and type <code>ipconfig /all</code>. On a Linux or Mac device, jump into the terminal and type <code>ifconfig</code>. Multiple MAC addresses? Your device might have several network interfaces like wired, wireless, and Bluetooth.
          </p>

          <div class="bg-purple-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-purple-300 mb-2">Steps to Find MAC Address:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Windows: Open command prompt, type <code>ipconfig /all</code></li>
              <li>Linux/Mac: Open terminal, type <code>ifconfig</code></li>
              <li>List multiple interfaces and their corresponding MAC addresses.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>