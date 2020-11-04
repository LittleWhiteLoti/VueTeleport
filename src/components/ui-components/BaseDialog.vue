<template>
    <teleport to="body">
        <div>
            <div @click="$emit('close')">
            </div>
            <header>
                <slot name="title">
                    {{ title }}
                </slot>
            </header>
            <section>
                <slot name="content">
                    {{ content }}
                </slot>
            </section>
            <menu>
                <slot name="action">
                    <button @click="action.click">
                        {{ action.content }}
                    </button>
                </slot>
            </menu>
        </div> 
    </teleport>
</template>

<script>
export default {
    
}
</script>