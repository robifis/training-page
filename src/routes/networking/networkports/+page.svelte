<script>
  import { Wifi, ChevronDown, ChevronUp, Server, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; // trigger reactivity
  };
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-3">
      <Server class="text-blue-400" size={36} />
      Network Ports Explained
    </h1>

    <!-- What are Ports Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('ports')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What are Ports?</h2>
        </div>
        <svelte:component this={expandedSections['ports'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['ports']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Ports aren't physical connections—they're logical. Think of them as specific slots where software services plug into a device to communicate over a network. Every port is tied to an IP address, acting as a gateway for specific data like web pages or files.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Ports are logical gateways used by services to communicate over a network, each tied to an IP address for routing.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Common Ports Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('common')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Common Ports</h2>
        </div>
        <svelte:component this={expandedSections['common'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['common']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Port numbers range from 0 to 65535, each assigned to specific services. Some popular ones include:
          </p>
          <ul class="list-disc list-inside text-gray-300 space-y-2">
            <li>Port 80: Used for HTTP web pages.</li>
            <li>Port 443: Used for HTTPS, secure web pages.</li>
            <li>Port 21: Used for FTP, file transfers.</li>
            <li>Port 25: Used for email services.</li>
          </ul>
        </div>
      {/if}
    </div>

    <!-- How Ports Work Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('how')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How Ports Work</h2>
        </div>
        <svelte:component this={expandedSections['how'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['how']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Ports and IP addresses go hand-in-hand. When you access a service, your request travels to the server's IP, and the port number tells it which service you need. For instance, typing "google.com" in your browser heads to Google's IP and uses port 80 to pull up the web page.
          </p>
        </div>
      {/if}
    </div>

    <!-- Using Ports: Real-Life Scenario Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('realLife')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Using Ports: Real-Life Scenario</h2>
        </div>
        <svelte:component this={expandedSections['realLife'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['realLife']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            While you don’t often see ports in action, they’re active every time you use the internet. Tools like Netstat can show you which ports your device is using at any moment. A display might reveal connections via ports 80 or 443, indicating web traffic, or port 21, suggesting file transfers.
          </p>

          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-blue-300 mb-2">Understanding Port Categories:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>System or Well-Known Ports (0-1023): Commonly used ports for standard services.</li>
              <li>Registered Ports (1024-49151): For specific services, registered by developers.</li>
              <li>Dynamic or Private Ports (49152-65535): Used dynamically by clients during sessions.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>