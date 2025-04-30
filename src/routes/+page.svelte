<!-- src/routes/+page.md -->
<script lang="ts">
    import { fade } from 'svelte/transition';
    import Container from '$lib/components/Container.svelte';
    import AnimationWrapper from '$lib/components/AnimationWrapper.svelte';
    import SidebarNav from '$lib/components/SidebarNav.svelte';
    import Section from '$lib/components/Section.svelte';
</script>

<SidebarNav/>

<div class="bg-blue-100 w-full">
    <AnimationWrapper>
        <Container className="space-y-12 text-center" expand={true}>
            <!-- Logo first -->
            <img
                    in:fade={{ delay: 200, duration: 500 }}
                    src="src/images/eidr-logo.png"
                    alt="EIDR Logo"
                    class="pt-64 pb-16 w-96 h-auto mx-auto"
            />

            <!-- Headline -->
            <h1
                    in:fade={{ delay: 400, duration: 500 }}
                    class="text-5xl pb-16 text-black"
            >
                Introducing the EIDR Python SDK
            </h1>

            <!-- Sections -->
            <div
                    class="flex flex-wrap justify-center items-stretch
               w-full max-w-8xl mx-auto mt-12 px-4
               gap-x-12 gap-y-16"
            >
                <Section
                        title="What is EIDR?"
                        className="w-full md:w-1/3"
                        delay={600}
                        duration={500}
                >
                    <p class="px-4 py-6 text-lg text-emerald-50 text-justify text-align-last-left">
                        <strong>EIDR</strong> (Entertainment Identifier Registry) is the global standard
                        for identifying audiovisual content—from feature films and TV episodes to
                        trailers and clips. It provides a stable, unique identifier that
                        simplifies metadata exchange across platforms and services.
                    </p>
                </Section>

                <Section
                        title="Why Python"
                        className="w-full md:w-1/3"
                        delay={900}
                >
                    <p class="px-4 py-6 text-lg text-emerald-50 text-justify text-align-last-left">
                        Python’s simplicity and <strong>rich ecosystem</strong> make it perfect for scripting
                        and automating interactions with EIDR’s REST API, whether you’re registering assets
                        or querying metadata.
                    </p>
                </Section>

                <Section
                        title="Use Cases"
                        className="w-full md:w-1/3"
                        delay={1200}
                >
                    <p class="px-4 py-6 text-lg text-emerald-50 text-justify text-align-last-left">
                        From <strong>bulk metadata enrichment</strong> to integration with broadcast workflows
                        and analytics pipelines—our SDK helps you build it in minutes.
                    </p>
                </Section>
            </div>

            <!-- Call to Action -->
            <div class="mt-16">
                <a
                        in:fade={{ delay: 1400, duration: 500 }}
                        href="/guides/intro"
                        class="inline-block bg-gradient-to-r from-primary to-secondary
                 text-contrast px-8 py-4 mt-16 rounded-lg
                 text-lg
                 shadow-xl transform transition
                 duration-300 ease-in-out
                 hover:scale-105 hover:shadow-2xl"
                >
                    Ready to try it out? <b>Start Here</b>
                </a>
            </div>

            <!-- Footer -->
            <footer class="mt-20 border-t bg-white py-6">
                <div
                        class="max-w-7xl mx-auto px-4
                 flex flex-col md:flex-row
                 justify-between items-center
                 text-sm text-gray-600
                 space-y-4 md:space-y-0"
                >
                    <div>© 2025 EIDR™</div>
                    <div>Developed by Alice, Bob, and Charlie</div>
                    <div>| Sponsored by Richard Kroon</div>
                </div>
            </footer>
        </Container>
    </AnimationWrapper>
</div>
