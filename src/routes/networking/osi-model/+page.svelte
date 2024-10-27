<script>
  import { ChevronDown, ChevronUp, Server, AlertCircle } from 'lucide-svelte';

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
      Demystifying the OSI Model
    </h1>

    <!-- Introduction to OSI Model Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('osi')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What is the OSI Model?</h2>
        </div>
        <svelte:component this={expandedSections['osi'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['osi']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            The OSI Model, or Open Systems Interconnection, is the ultimate guide for understanding how networks communicate. Imagine it as the master blueprint, a seven-layer cake, where each slice holds a unique part of the comms world. These layers help us pinpoint what's happening when tech goes rogue or when systems sync like magic.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              OSI Model breaks network functions into seven layers, guiding data communication from the user to the wire.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- The 7 Layers Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('layers')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The 7 Layers</h2>
        </div>
        <svelte:component this={expandedSections['layers'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['layers']}
        <div class="p-4">
          <div class="grid gap-4 mb-4">
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 7: Application</h4>
              <p class="text-gray-300">This is where we access network services. Think web browsers, email clients, and apps like Outlook and Skype.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 6: Presentation</h4>
              <p class="text-gray-300">Handles data translation and encryption. It ensures data is readable by the application layer.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 5: Session</h4>
              <p class="text-gray-300">Manages sessions between apps. Sets up, coordinates, and terminates connections.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 4: Transport</h4>
              <p class="text-gray-300">Dictates how much data to send, error-checks, and ensures data is delivered reliably through TCP/UDP.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 3: Network</h4>
              <p class="text-gray-300">Routes data packets via addresses. Uses protocols like IP to get your data where it needs to go.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 2: Data Link</h4>
              <p class="text-gray-300">Ensures error-free transmission from one node to another in your local network. Think Ethernet and Wi-Fi protocols.</p>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">Layer 1: Physical</h4>
              <p class="text-gray-300">Deals with the physical components like cables, switches, and the wireless spectrum. Is everything plugged in?</p>
            </div>
          </div>
        </div>
      {/if}
    </div>

    <!-- Why You Should Care Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('importance')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">Why You Should Care</h2>
        </div>
        <svelte:component this={expandedSections['importance'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['importance']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Understanding the OSI model is like having the ultimate cheat-sheet for diagnosing network issues and building systems that just work. It's the secret sauce for tech wizards and IT ninjas. Dive into each layer to become the troubleshooting guru you've always wanted to be.
          </p>

          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-blue-300 mb-2">Takeaways:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Simplifies troubleshooting by isolating issues to specific layers.</li>
              <li>Facilitates the development of interoperable tech products.</li>
              <li>Empowers you to understand network communications better.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>