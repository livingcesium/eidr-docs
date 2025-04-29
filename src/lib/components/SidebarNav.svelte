
<script context="module" lang="ts">
    export interface NavItem {
        logo: string | null;
        label: string;
        route: string;
        children?: NavItem[];
    }

    export const defaultOptions: Record<string, NavItem> = {
        guides: {
            logo: null,
            label: 'Guides',
            route: '/guides',
            children: [
                { logo: null, label: 'Introduction',    route: '/guides/intro' },
                { logo: null, label: 'Getting Started', route: '/guides/start' },
            ]
        },
        config: { logo: null, label: 'Config',       route: '/docs/config' },
        manager: { logo: null, label: 'Manager',       route: '/docs/manager' },
        driver: { logo: null, label: 'Driver',       route: '/docs/driver' },
        services: { logo: null, label: 'Services',       route: '/docs/services', children: [
                { logo: null, label: 'Interface',       route: '/docs/services/interface' },
                { logo: null, label: 'EIDR Request',       route: '/docs/services/eidr_request' },
                { logo: null, label: 'Status Request',       route: '/docs/services/status_request' },
                { logo: null, label: 'Graph Traversal',       route: '/docs/services/graph_traversal' },
                { logo: null, label: 'Query',       route: '/docs/services/query' },
                { logo: null, label: 'Service Query',       route: '/docs/services/service_query' },
                { logo: null, label: 'Response Reader',       route: '/docs/services/response_reader' },
                { logo: null, label: 'Metadata',       route: '/docs/services/metadata' },
                { logo: null, label: 'Simple Metadata',       route: '/docs/services/simple_metadata' },
                { logo: null, label: 'No Operation Request',       route: '/docs/services/no_op' },
                { logo: null, label: 'Party Query',       route: '/docs/services/party_query' },
            ] },
        registration_services: { logo: null, label: 'Registration',       route: '/docs/services/registration', children: [
                { logo: null, label: 'Create',       route: '/docs/services/registration/create' },
                { logo: null, label: 'Delete',       route: '/docs/services/registration/delete' },
                { logo: null, label: 'Modify',       route: '/docs/services/registration/modify' },
                { logo: null, label: 'Alias',       route: '/docs/services/registration/alias' },
                { logo: null, label: 'Promote',       route: '/docs/services/registration/promote' },
                { logo: null, label: 'Add Relationship',       route: '/docs/services/registration/add_relationship' },
                { logo: null, label: 'Replace Relationship',       route: '/docs/services/registration/replace_relationship' },
            ] }
    };
    export const ACTIVE_CLASSES   = 'bg-primary-dark';
    export const INACTIVE_CLASSES = '';
</script>

<script lang="ts">
    import { fly } from 'svelte/transition';
    import { page} from '$app/stores';


    export let options: Record<string, NavItem> = defaultOptions;
    $: current = $page.url.pathname.replace(/\/$/, '') || '/';
    const isActive  = (route: string) =>
        route.replace(/\/$/, '') === current;

    const isParentActive = (item: NavItem | undefined): boolean =>
        !!item && ((isActive(item.route) || item.children?.some((item) => isActive(item.route))) ?? false);

    const linkClass = (active: boolean) =>
        active ? ACTIVE_CLASSES : INACTIVE_CLASSES;
</script>

<!-- wrapper that controls the peek/slide behaviour -->
<div class="fixed top-4 left-0 h-[calc(100vh-2rem)] w-32 group z-50">
    <nav
            class="absolute top-0 left-0 h-full w-64
           bg-primary bg-opacity-10 backdrop-blur-md
           rounded-lg shadow-lg overflow-auto
           transform -translate-x-[calc(100%-1rem)]
           group-hover:translate-x-0
           transition-transform duration-300 ease-out"
    >
        <ul class="p-4 space-y-3">
            {#if $page.url.pathname !== '/'}
                <li>
                    <a
                            href="/"
                            class="flex items-center px-3 py-2 rounded-md
                   transition-colors duration-150"
                    >
                        <span class="text-primary font-medium">Home</span>
                    </a>
                </li>
            {/if}

            {#each Object.values(options) as item}
                <li>
                    <a
                            href={item.route}
                            class="flex items-center px-3 py-2 rounded-md
                   transition-colors duration-150
                   {linkClass(isParentActive(item))}"
                    >
                        {#if item.logo}
                            <img src={item.logo} alt="{item.label} icon" class="w-5 h-5 mr-2" />
                        {/if}
                        <span class="text-primary font-medium">{item.label}</span>
                    </a>

                    {#if item.children}
                        <ul class="mt-1 ml-6 space-y-1 bg-opacity-5 p-2 rounded">
                            {#each item.children as child}
                                <li>
                                    <a
                                            href={child.route}
                                            class="block text-sm px-2 py-1 rounded
                           transition-colors duration-150
                           {isActive(child.route) ? 'underline' : ''}
                           text-primary"
                                    >
                                        {child.label}
                                    </a>
                                </li>
                            {/each}
                        </ul>
                    {/if}
                </li>
            {/each}
        </ul>
    </nav>
</div>
