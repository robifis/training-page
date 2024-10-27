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
      TCP vs UDP Explained
    </h1>

    <!-- Introduction to TCP Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('tcp')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">TCP: Ensuring Reliable Communication</h2>
        </div>
        <svelte:component this={expandedSections['tcp'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['tcp']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            TCP, or Transmission Control Protocol, is the go-to choice for ensuring that data packets arrive intact and in order. Picture downloading a file—TCP makes sure you get the entire file, not just bits and pieces. It's like a reliable courier who ensures every part of your package is delivered.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              TCP guarantees that data is received completely and in the correct order through a connection-oriented approach using a three-way handshake.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- The Three-Way Handshake Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('handshake')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The Three-Way Handshake</h2>
        </div>
        <svelte:component this={expandedSections['handshake'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['handshake']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Before data starts flowing, TCP sets up a connection via the three-way handshake:
          </p>
          <ul class="list-disc list-inside text-gray-300 space-y-2">
            <li>SYN: The sender requests a connection.</li>
            <li>ACK: The receiver acknowledges with a response.</li>
            <li>Sender re-affirms with a final ACK.</li>
          </ul>
          <p class="text-gray-300 leading-relaxed mt-4">
            This ensures both machines are ready, establishing a reliable path for data.
          </p>
        </div>
      {/if}
    </div>

    <!-- Introduction to UDP Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('udp')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">UDP: Speed Over Accuracy</h2>
        </div>
        <svelte:component this={expandedSections['udp'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['udp']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            UDP, or User Datagram Protocol, ditches the handshake, sending data without ensuring receipt. Think of it as tossing a note out the window and hoping it lands in the right hands. It's faster due to less overhead, ideal for scenarios where speed trumps reliability.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              UDP sacrifices reliability for speed, sending packets without establishing a connection. Known as the "fire-and-forget" protocol.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- TCP vs. UDP: A Quick Comparison Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button 
        on:click={() => toggleSection('comparison')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">TCP vs. UDP: A Quick Comparison</h2>
        </div>
        <svelte:component this={expandedSections['comparison'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>
      
      {#if expandedSections['comparison']}
        <div class="p-4">
          <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mb-4">
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">TCP</h4>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>Connection-oriented</li>
                <li>Reliable data delivery</li>
                <li>Ideal for webpages, emails, file transfers</li>
              </ul>
            </div>
            <div class="bg-gray-700 p-4 rounded-lg">
              <h4 class="text-blue-300 font-semibold mb-2">UDP</h4>
              <ul class="list-disc list-inside text-gray-300 space-y-2">
                <li>Connection-less</li>
                <li>Faster, but no delivery guarantee</li>
                <li>Used in real-time applications like games or streaming</li>
              </ul>
            </div>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>