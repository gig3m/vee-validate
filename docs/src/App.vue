<template>
    <div id="layout" ref="layout">
        <!-- Menu toggle -->
        <a href="#menu" id="menuLink" class="menu-link" ref="menuLink">
            <!-- Hamburger icon -->
            <span></span>
        </a>

        <div id="menu" ref="menu">
            <div class="pure-menu">
                <a href="/" class="pure-menu-heading">Vee Validate</a>
                <ul class="pure-menu-list">
                    <li class="pure-menu-item">
                        <a href="index.html" class="pure-menu-link">Getting Started</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="index.html#installation" class="pure-menu-link">Installation</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="index.html#basic-example" class="pure-menu-link">Basic Example</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="index.html#render-errors" class="pure-menu-link">Rendering Errors</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="examples.html" class="pure-menu-link">Examples</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="rules.html" class="pure-menu-link">Validation Rules</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="localization.html" class="pure-menu-link">Localization</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="api.html" class="pure-menu-link">API Reference</a>
                    </li>
                    <li class="pure-menu-item">
                        <a href="index.html#configuration" class="pure-menu-link">Configuration</a>
                    </li>
                </ul>
            </div>
            <div class="about flex-center">
                <a target="github" href="https://github.com/logaretm/vee-validate"><i class="icon-github"></i></a>
            </div>
        </div>

        <div id="main">
            <div class="header">
                <h1>{{ heading }}</h1>
                <h2>{{ subtitle }}</h2>
            </div>
            <div class="content">
                <slot></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['heading', 'subtitle'],

    mounted() {
        const layout = this.$refs.layout;
        const menu = this.$refs.menu;
        const menuLink = this.$refs.menuLink;

        const toggleClass = (element, className) => {
            const classes = element.className.split(/\s+/);
            const length = classes.length;

            for(let i = 0; i < length; i++) {
                if (classes[i] === className) {
                    classes.splice(i, 1);
                    break;
                }
            }
            // The className is not found
            if (length === classes.length) {
                classes.push(className);
            }

            element.className = classes.join(' ');
        }

        menuLink.onclick = (e) => {
            const active = 'active';

            e.preventDefault();
            toggleClass(layout, active);
            toggleClass(menu, active);
            toggleClass(menuLink, active);
        };
    }
}
</script>
