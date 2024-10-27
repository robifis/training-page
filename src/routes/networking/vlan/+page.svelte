<script>
  import { Wifi, ChevronDown, ChevronUp, Home, Server, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; 
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-3">
      <Wifi class="text-blue-400" size={36} />
      VLANs Explained: Secure Your Network
    </h1>

    <!-- Introduction Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Introduction</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Ever wondered about VLANs and their importance? If you're playing with smart home gadgets, VLANs are something to consider.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              VLANs split a network into smaller parts, boosting security and performance. They're great for separating IoT devices from personal data.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- How VLANs Work Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('how')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <Server class="text-blue-400" size={24} />
          <h2 class="text-xl font-semibold text-gray-100">How VLANs Work</h2>
        </div>
        <svelte:component this={expandedSections['how'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['how']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            VLANs operate like separate lanes on a highway, all sharing the same space but carrying different traffic. Each packet gets a unique tag, directing it to its proper VLAN.
          </p>
          
          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-blue-300 mb-2">Benefits of VLANs:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Improved security by isolating sensitive data</li>
              <li>Enhanced performance through reduced broadcast traffic</li>
              <li>Better network management and adaptability</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Setting Up VLANs Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('setup')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <Home class="text-blue-400" size={24} />
          <h2 class="text-xl font-semibold text-gray-100">Setting Up VLANs</h2>
        </div>
        <svelte:component this={expandedSections['setup'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['setup']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Start by defining VLANs on your switches and assigning unique IDs. Configure your router for VLAN routing if needed.
          </p>
          
          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-blue-300 mb-2">Key Setup Steps:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Define VLANs with unique IDs</li>
              <li>Configure network ports for each VLAN</li>
              <li>Set up VLAN routing for intercommunication</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>

    <!-- Real-Life Examples & Usage Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('examples')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <AlertCircle class="text-blue-400" size={24} />
          <h2 class="text-xl font-semibold text-gray-100">Real-Life Examples & Usage</h2>
        </div>
        <svelte:component this={expandedSections['examples'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['examples']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            VLANs keep smart home gadgets separate from personal files. They're also used in offices to isolate different departments or guest Wi-Fi.
          </p>

          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-blue-300 mb-2">Common Misconceptions:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>VLANs aren't a complete security solution.</li>
              <li>They simplify management with proper planning.</li>
              <li>No significant performance overhead on modern hardware.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>