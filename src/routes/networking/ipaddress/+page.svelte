<script>
  import { Server, ChevronDown, ChevronUp, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections;
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-3">
      <Server class="text-blue-400" size={36} />
      What is an IP Address?
    </h1>

    <!-- What is an IP Address Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The Basics</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            IP addresses are the magic numbers behind the curtain of the internet, allowing devices to communicate with each other. Think of an IP address like a phone number for your device. It's the way everything—phones, computers, and even smart light bulbs—gets on the internet and talks to each other.
          </p>
          <p class="text-gray-300 leading-relaxed mb-4">
            Without an IP address, devices can't connect or communicate online. Think of it as the universal language that devices use to share memes, stream movies, or send status updates to your smartwatch.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              An IP address is like a unique phone number for your device, necessary for online communication.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- How IP Addresses are Assigned Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('assigned')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How They're Assigned</h2>
        </div>
        <svelte:component this={expandedSections['assigned'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['assigned']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Every time a device joins a network, it receives an IP address via DHCP—a process akin to being given a token of access by the network's router, much like Oprah handing out items on a show: “You get an IP address, and you get an IP address!”
          </p>
          <p class="text-gray-300 leading-relaxed mb-4">
            Usually, these IPs start with common numbers like 192.168.1, thanks to the settings dictated by your router and the subnet mask—an important figure in defining network boundaries.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Devices get their IP addresses from the router via DHCP, commonly starting with numbers like 192.168.1.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Network and Host Portions Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('networkHost')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Network vs Host</h2>
        </div>
        <svelte:component this={expandedSections['networkHost'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['networkHost']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            In an IP address, the subnet mask helps identify the network and host portions. The numbers 255 in the subnet mask denote network areas that remain constant across devices (your network's street name), while the final bit allows variation (your device’s house number).
          </p>
          <p class="text-gray-300 leading-relaxed mb-4">
            This distinction is crucial for devices to discern whether they need to communicate within the network directly or reach out to a router to connect elsewhere.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Network portions (255s) stay the same; host portions change, defined by the subnet mask to organize connections.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Sending Data and Default Gateway Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('dataGateway')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Data Paths & Gateways</h2>
        </div>
        <svelte:component this={expandedSections['dataGateway'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['dataGateway']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Much like walking next door with a coffee to share, devices check if others are on the same ‘network street’ to directly transfer data. But when reaching someone ‘out of town’, like a website, your device routes the message through the default gateway or router, handling the magic of long-distance communication.
          </p>
          <p class="text-gray-300 leading-relaxed mb-4">
            Routers know the way to any destination, much like a skilled conductor ensuring everything gets to its intended endpoint smoothly.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Devices use IPs to check local addresses directly; routers manage routes to distant networks.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- IP Address Calculation Challenge Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('challenge')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">IP Calculation Challenge</h2>
        </div>
        <svelte:component this={expandedSections['challenge'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['challenge']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            With a typical home network like 192.168.1.x where x marks the changeable host portion, determine usable IP addresses. Subtract from 256 for reserved network and broadcast addresses and one for the router. How many do you get?
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Calculate total IPs: 256 minus network, broadcast, and router addresses, typically resulting in 253 usable addresses.
            </p>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>