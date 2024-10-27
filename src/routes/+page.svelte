<script>
    import { BookOpen, Wifi, ArrowRight } from 'lucide-svelte';

    const overview = [
        {
            title: 'Networking Fundamentals',
            description: 'Learn the core concepts of networking, including how devices communicate over networks, the different protocols involved, and the models used to understand network structures.',
            url: '/networking'
        },
        {
            title: 'Advanced Configuration',
            description: 'Dive deeper into network configuration settings, learn how to set up VLANs, manage NAT, and understand how DHCP and DNS work in detail.',
            url: '/networking/configuration'
        }
    ];
</script>

<div class="min-h-screen bg-gray-900 text-gray-100">
    <div class="container mx-auto px-4 py-8 max-w-4xl">
        <h1 class="text-4xl font-bold text-blue-400 mb-8 flex items-center gap-2">
            <BookOpen class="text-blue-400" size={36} />
            Welcome to the Learning Hub
        </h1>
        <p class="text-lg text-gray-300 mb-8">
            Explore a collection of resources designed to enhance your understanding of networking. Whether you're learning the basics or delving into advanced configurations, this hub provides a structured path to deepen your knowledge.
        </p>

        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
            {#each overview as section}
                <div class="bg-gray-800 p-6 rounded-lg shadow-lg hover:shadow-xl transition">
                    <h2 class="text-2xl font-semibold text-blue-500 mb-4">{section.title}</h2>
                    <p class="text-gray-300 mb-4">{section.description}</p>
                    <a href={section.url} class="flex items-center text-blue-400 hover:text-blue-300 transition-colors">
                        <span>Explore {section.title}</span>
                        <ArrowRight class="ml-2" size={20} />
                    </a>
                </div>
            {/each}
        </div>
    </div>
</div>