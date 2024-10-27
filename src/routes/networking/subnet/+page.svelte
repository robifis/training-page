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
      Subnet Mask
    </h1>

    <!-- Introduction Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Setting the Scene</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Subnet masks might sound mysterious, but they're actually pretty straightforward once you break them down. Think of a subnet mask as a magical divider between the network portion and the host portion of an IP address. This means it determines how big your network is and how many 'nodes' or devices you can have. Every IP address has a subnet mask that helps define its network boundaries.
          </p>
          <p class="text-gray-300 leading-relaxed mb-4">
            Now, to get into the geeky details, subnet masks use binary language – that's strings of 1s and 0s. You'll often see numbers like 255 in a subnet mask. These numbers in decimal correspond to a full set of 1s in binary. When you see 255, it means that portion of the network is fixed; it doesn't change. Conversely, 0s in the mask indicate flexibility, allowing you to add devices as hosts on your network.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              A subnet mask splits your IP address into network and host parts using 1s and 0s in binary, defining how many devices you can host and what remains constant.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Calculations Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('calculations')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Subnet Mask Calculations</h2>
        </div>
        <svelte:component this={expandedSections['calculations'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['calculations']}
        <div class="p-4">
          <h3 class="text-lg font-semibold text-blue-300 mb-2">Binary Basics</h3>
          <p class="text-gray-300 leading-relaxed mb-4">
            Convert subnet masks into binary to understand network size. When you break down 255 into binary, you get 11111111. All 1s show that part of the address is strictly for the network. Hence, for an IP like 255.255.255.0, the first three sections are network bits, and the last one is for hosts.
          </p>

          <h3 class="text-lg font-semibold text-blue-300 mb-2">Determine Host Capacity</h3>
          <p class="text-gray-300 leading-relaxed mb-4">
            Calculate how many devices your network can support by focusing on the 0s in an IP address. For the decimal subnet 255.255.255.0, the last octet is 0, equivalent to eight 0s in binary – this octet dictates the host range. Use the formula: 2^(number of 0s) - 2. For our example with eight 0s, that means 2^8 - 2 = 256 - 2 = 254 usable IP addresses.
          </p>

          <h3 class="text-lg font-semibold text-blue-300 mb-2">Adjust Network Size</h3>
          <p class="text-gray-300 leading-relaxed mb-4">
            If you need more host capacity, convert a network bit (1) to a host bit (0). This increases the number of available host IPs. For example, changing a 11111111 (255) to 11111110 (254) in binary opens up more room for hosts, offering more usable addresses.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Subnet masks define your network size and device capacity using binary 1s and 0s. The magic formula is 2^(number of 0s) - 2 for calculating hosts.
            </p>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>