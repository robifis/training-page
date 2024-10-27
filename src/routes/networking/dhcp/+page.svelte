<script>
    import { Wifi, ChevronDown, ChevronUp, Coffee, Home, Server, AlertCircle } from 'lucide-svelte';
  
    // Track expanded sections
    let expandedSections = {};
  
    const toggleSection = (id) => {
      expandedSections[id] = !expandedSections[id];
      expandedSections = expandedSections; // trigger reactivity
    };
  </script>
  
  <div class="min-h-screen bg-gray-900 text-gray-100">
    <div class="container mx-auto px-4 py-8 max-w-4xl">
      <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-3">
        <Wifi class="text-blue-400" size={36} />
        DHCP: Dynamic Host Configuration Protocol 
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
              Have you ever wondered how your device gets its network settings automatically when you connect to a Wi-Fi network? That's DHCP in action! The Dynamic Host Configuration Protocol (DHCP) is like a friendly network butler that hands out network settings to devices when they join a network.
            </p>
            
            <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
              <div class="flex items-center gap-2 mb-2">
                <AlertCircle class="text-blue-400" size={20} />
                <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
              </div>
              <p class="text-blue-100">
                DHCP automatically configures network settings so you don't have to do it manually.
              </p>
            </div>
          </div>
        {/if}
      </div>
  
      <!-- What is DHCP Section -->
      <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
        <button 
          on:click={() => toggleSection('what')}
          class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
        >
          <div class="flex items-center gap-3">
            <Server class="text-blue-400" size={24} />
            <h2 class="text-xl font-semibold text-gray-100">What is DHCP?</h2>
          </div>
          <svelte:component this={expandedSections['what'] ? ChevronUp : ChevronDown} class="text-gray-400" />
        </button>
        
        {#if expandedSections['what']}
          <div class="p-4">
            <p class="text-gray-300 leading-relaxed mb-4">
              Think of DHCP as an automated reception desk for your network. When a new device (like your phone or laptop) connects, instead of you having to manually type in all the network settings, DHCP automatically provides everything needed to get online.
            </p>
            
            <div class="bg-gray-700 rounded-lg p-4 mb-4">
              <h4 class="text-lg font-semibold text-blue-300 mb-2">DHCP provides:</h4>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>An IP address (your device's unique network identity)</li>
                <li>A subnet mask (defines your local network's size)</li>
                <li>A default gateway (your route to the internet)</li>
                <li>DNS server information (helps translate website names into IP addresses)</li>
              </ul>
            </div>
          </div>
        {/if}
      </div>
  
      <!-- How DHCP Works Section -->
      <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
        <button 
          on:click={() => toggleSection('how')}
          class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
        >
          <div class="flex items-center gap-3">
            <Server class="text-blue-400" size={24} />
            <h2 class="text-xl font-semibold text-gray-100">How DHCP Works</h2>
          </div>
          <svelte:component this={expandedSections['how'] ? ChevronUp : ChevronDown} class="text-gray-400" />
        </button>
        
        {#if expandedSections['how']}
          <div class="p-4">
            <p class="text-gray-300 leading-relaxed mb-4">
              The process follows a four-step dance, often called DORA:
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
              {#each [
                {
                  step: "1. Discover",
                  desc: "Your device broadcasts a message saying 'Hello! I need network settings!'"
                },
                {
                  step: "2. Offer",
                  desc: "The DHCP server responds with 'I can give you these settings...'"
                },
                {
                  step: "3. Request",
                  desc: "Your device says 'Yes, I'd like those settings, please!'"
                },
                {
                  step: "4. Acknowledge",
                  desc: "The server confirms 'They're yours to use!'"
                }
              ] as item}
                <div class="bg-gray-700 p-4 rounded-lg">
                  <h4 class="text-blue-300 font-semibold mb-2">{item.step}</h4>
                  <p class="text-gray-300">{item.desc}</p>
                </div>
              {/each}
            </div>
          </div>
        {/if}
      </div>
  
      <!-- Real-World Examples Section -->
      <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
        <button 
          on:click={() => toggleSection('examples')}
          class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
        >
          <div class="flex items-center gap-3">
            <Coffee class="text-blue-400" size={24} />
            <h2 class="text-xl font-semibold text-gray-100">Real-World Examples</h2>
          </div>
          <svelte:component this={expandedSections['examples'] ? ChevronUp : ChevronDown} class="text-gray-400" />
        </button>
        
        {#if expandedSections['examples']}
          <div class="p-4 space-y-6">
            <div>
              <h3 class="text-lg font-semibold text-blue-300 mb-2">Coffee Shop Scenario</h3>
              <p class="text-gray-300 leading-relaxed mb-4">
                When you visit a coffee shop, your phone automatically gets online because:
              </p>
              <ol class="list-decimal list-inside text-gray-300 space-y-2">
                <li>You connect to the Wi-Fi</li>
                <li>Your phone uses DHCP to get network settings</li>
                <li>You can browse the internet without any manual configuration</li>
              </ol>
            </div>
  
            <div>
              <h3 class="text-lg font-semibold text-blue-300 mb-2">Home Network Example</h3>
              <p class="text-gray-300 leading-relaxed mb-4">
                Your smart home devices (cameras, speakers, smart lights) all use DHCP to:
              </p>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>Get unique IP addresses automatically</li>
                <li>Connect to your network without manual setup</li>
                <li>Communicate with other devices seamlessly</li>
              </ul>
            </div>
          </div>
        {/if}
      </div>
  
      <!-- Important Concepts Section -->
      <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
        <button 
          on:click={() => toggleSection('concepts')}
          class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
        >
          <div class="flex items-center gap-3">
            <Home class="text-blue-400" size={24} />
            <h2 class="text-xl font-semibold text-gray-100">Important Concepts</h2>
          </div>
          <svelte:component this={expandedSections['concepts'] ? ChevronUp : ChevronDown} class="text-gray-400" />
        </button>
        
        {#if expandedSections['concepts']}
          <div class="p-4 space-y-6">
            <div>
              <h3 class="text-lg font-semibold text-blue-300 mb-2">IP Address Leasing</h3>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>DHCP assigns addresses for a specific time period (the lease)</li>
                <li>Devices try to renew their lease halfway through</li>
                <li>Helps manage limited IP addresses efficiently</li>
                <li>Typical lease times:
                  <ul class="list-disc list-inside ml-6 mt-2">
                    <li>Home networks: 24 hours to 7 days</li>
                    <li>Public spaces: Shorter periods</li>
                  </ul>
                </li>
              </ul>
            </div>
  
            <div>
              <h3 class="text-lg font-semibold text-blue-300 mb-2">Static vs Dynamic</h3>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>Servers typically use static (manually set) IP addresses</li>
                <li>Client devices usually use dynamic (DHCP-assigned) addresses</li>
                <li>Home devices almost always use DHCP</li>
              </ul>
            </div>
  
            <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
              <div class="flex items-center gap-2 mb-2">
                <AlertCircle class="text-blue-400" size={20} />
                <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
              </div>
              <ul class="list-disc list-inside text-blue-100 space-y-2">
                <li>DHCP uses UDP ports 67 and 68</li>
                <li>Follows the DORA process (Discover, Offer, Request, Acknowledge)</li>
                <li>Provides IP address, subnet mask, gateway, and DNS information</li>
                <li>Includes lease timing for address management</li>
              </ul>
            </div>
          </div>
        {/if}
      </div>
    </div>
  </div>