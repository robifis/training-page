<script>
  import { ChevronDown, ChevronUp, Database, AlertCircle } from 'lucide-svelte';

  let expandedSections = {};

  const toggleSection = (id) => {
    expandedSections[id] = !expandedSections[id];
    expandedSections = expandedSections; // trigger reactivity
  };
</script>
<div class="min-h-screen bg-gray-900 text-gray-100">
  <div class="container mx-auto px-4 py-8 max-w-4xl">
    <h1 class="text-4xl font-bold text-teal-400 mb-8 flex items-center gap-3">
      <Database class="text-teal-400" size={36} />
      Exploring the World of DNS Records
    </h1>

    <!-- Introduction to DNS Records Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('intro')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">What are DNS Records?</h2>
        </div>
        <svelte:component this={expandedSections['intro'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['intro']}
        <div class="p-4">
          <p class="text-gray-300 leading-relaxed mb-4">
            DNS Records are like the magic spells of the internet, translating human-friendly domain names into the IP addresses that computers understand. Essential for navigating the vast web, these records store all the necessary information to direct your queries to the right destinations.
          </p>

          <div class="bg-teal-900/50 border border-teal-700 rounded-lg p-4 my-4">
            <div class="flex items-center gap-2 mb-2">
              <AlertCircle class="text-teal-400" size={20} />
              <h3 class="text-lg font-semibold text-teal-300">TLDR</h3>
            </div>
            <p class="text-teal-100">
              DNS Records act as the internet's phonebook, translating domain names into IP addresses, enabling seamless web navigation.
            </p>
          </div>
        </div>
      {/if}
    </div>

    <!-- Common DNS Records Section -->
    <div class="mb-6 bg-gray-800 rounded-lg overflow-hidden">
      <button
        on:click={() => toggleSection('dnsRecords')}
        class="w-full p-4 flex items-center justify-between bg-gray-700 hover:bg-gray-600 transition-colors"
      >
        <div class="flex items-center gap-3">
          <h2 class="text-xl font-semibold text-gray-100">The Most Common DNS Records</h2>
        </div>
        <svelte:component this={expandedSections['dnsRecords'] ? ChevronUp : ChevronDown} class="text-gray-400" />
      </button>

      {#if expandedSections['dnsRecords']}
        <div class="p-4">
          <!-- A Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">A Record</h4>
            <p class="text-gray-300">The A record is your DNS go-to for saying “this domain name means this IPv4 address.” It’s like your phonebook lookup for web addresses.</p>
          </div>
          <!-- AAAA Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">AAAA Record</h4>
            <p class="text-gray-300">Similar to the A record, the AAAA record points domain names to IPv6 addresses. Think of it as the upgrade from the old to the new internet era.</p>
          </div>
          <!-- CNAME Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">CNAME Record</h4>
            <p class="text-gray-300">CNAME, or Canonical Name record, is like a nickname, aliasing one domain name to another. Perfect for when you need multiple domains pointing to the same place!</p>
          </div>
          <!-- MX Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">MX Record</h4>
            <p class="text-gray-300">The Mail Exchanger record is the post office of the DNS world, directing emails to the appropriate mail servers for delivery. Simplified email routing magic!</p>
          </div>
          <!-- SOA Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">SOA Record</h4>
            <p class="text-gray-300">The Start of Authority record holds essential details about the domain, like the admin’s email and the zone serial number. The overseer of DNS records.</p>
          </div>
          <!-- NS Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">NS Record</h4>
            <p class="text-gray-300">Name Server records point to the DNS servers that hold the authoritative data for a domain, guiding queries to the source of truth in the DNS realm.</p>
          </div>
          <!-- PTR Record -->
          <div class="bg-gray-700 p-4 rounded-lg mb-4">
            <h4 class="text-teal-300 font-semibold mb-2">PTR Record</h4>
            <p class="text-gray-300">PTR records are like A records in reverse, translating IP addresses back into domain names for authentication and spam prevention - think reverse lookup magic!</p>
          </div>
          <!-- TXT Record -->
          <div class="bg-gray-700 p-4 rounded-lg">
            <h4 class="text-teal-300 font-semibold mb-2">TXT Record</h4>
            <p class="text-gray-300">This record holds text for various purposes, from SPF authentication to DMARC, it’s the Swiss Army Knife of DNS, delivering diverse textual data as needed.</p>
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
            Understanding DNS Records is pivotal—it's the key to mastering internet navigation and troubleshooting. Whether you're setting up a website, managing email servers, or fortifying security, these records empower you to ensure seamless digital interactions.
          </p>

          <div class="bg-gray-700 rounded-lg p-4 mb-4">
            <h4 class="text-lg font-semibold text-teal-300 mb-2">Takeaways:</h4>
            <ul class="list-disc list-inside text-gray-300 space-y-2">
              <li>Critical for navigating and configuring internet services.</li>
              <li>Essential for troubleshooting connectivity issues.</li>
              <li>Vital for email routing and security measures.</li>
            </ul>
          </div>
        </div>
      {/if}
    </div>
  </div>
</div>