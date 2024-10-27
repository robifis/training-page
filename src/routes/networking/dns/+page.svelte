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
      What is DNS?
    </h1>

    <!-- What is DNS Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The Basics</h2>
        </div>
        <svelte:component
          this={expandedSections['intro'] ? ChevronUp : ChevronDown}
          class="text-gray-400"
        />
      </button>

      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            DNS, or Domain Name System, is like the internet's contact app. It translates human-friendly domain names, like academy.networkchuck.com, into IP addresses, which computers use to identify each other on the network. Without DNS, you'd need to remember numeric IP addresses for every site you want to visit, which is practically impossible.
          </p>
          
          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              DNS maps domain names to IP addresses, acting as the internet’s phonebook.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- How DNS Works Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('howItWorks')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">How DNS Works</h2>
        </div>
        <svelte:component
          this={expandedSections['howItWorks'] ? ChevronUp : ChevronDown}
          class="text-gray-400"
        />
      </button>

      {#if expandedSections['howItWorks']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            When you enter a web address, your computer consults its DNS server, much like checking a phonebook for a friend's number. This DNS server may already have the IP address cached. If not, it acts as a recursive resolver, asking root servers, then TLD servers, and finally authoritative DNS servers to find the IP that matches your domain request.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              DNS servers query a hierarchy of other servers to resolve domain names to IP addresses.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- DNS Security Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('security')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">DNS Security</h2>
        </div>
        <svelte:component
          this={expandedSections['security'] ? ChevronUp : ChevronDown}
          class="text-gray-400"
        />
      </button>

      {#if expandedSections['security']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Traditional DNS queries are unencrypted, making them vulnerable to attacks like DNS spoofing. Solutions like DNS over HTTPS (DoH) encrypt DNS queries, preventing eavesdroppers from snooping on your browsing history.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              Secure your DNS with protocols like DoH to encrypt and protect queries from prying eyes.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- DNS Records Explained Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('records')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">DNS Records Explained</h2>
        </div>
        <svelte:component
          this={expandedSections['records'] ? ChevronUp : ChevronDown}
          class="text-gray-400"
        />
      </button>

      {#if expandedSections['records']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            DNS operates with several types of records, including A records (domain to IP mapping), MX records (email routing), CNAME (alias records), and TXT records (verification and policies). Each plays a vital role in how domain information is handled across the web.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              DNS records manage everything from domain-IP mapping to email routing.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- DNS Configuration Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('configuration')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">DNS Configuration and Management</h2>
        </div>
        <svelte:component
          this={expandedSections['configuration'] ? ChevronUp : ChevronDown}
          class="text-gray-400"
        />
      </button>

      {#if expandedSections['configuration']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            Managing DNS involves setting up authoritative DNS servers, configuring records, and ensuring security protocols like DOH are in place. This process can be complex, involving registrars, TLD updates, and zone file management.
          </p>

          <div class="bg-blue-900/50 border border-blue-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-blue-400" size={20} />
              <h3 class="text-lg font-semibold text-blue-300">TLDR</h3>
            </div>
            <p class="text-blue-100">
              DNS management requires configuring servers, updating TLDs, and setting security protocols.
            </p>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>