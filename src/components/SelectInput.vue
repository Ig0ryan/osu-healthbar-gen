<template>
    <div class="field">
        <label v-if="label" class="label" :for="componentid">{{ label }}</label>
        <div :class="{ 'control': true, 'has-icons-left': iconleft}">
            <div :class="['select', errorstatus]">
                <select :value="value"
                        :disabled="!enabled"
                        :id="componentid"
                        @input="$emit('input', $event.target.value)">

                    <option v-for="opt in options" :value="opt.value">
                        {{ opt.name }}
                    </option>
                    
                </select>
                <span v-if="iconleft" class="icon is-small is-left">
                    <font-awesome-icon :icon="iconleft" />
                </span>
            </div>
        </div>
        <p v-if="errorstring" :class="['help', errorstatus]">{{ errorstring }}</p>
    </div>
</template>

<script>
import FontAwesomeIcon from '@fortawesome/vue-fontawesome'


export default {

    components: { FontAwesomeIcon },

    props: {
        value: { default: '' },
        label: { default: '' },
        options: { default: [], },
        errorstring: { default: '' },
        errorstatus: { default: '' },
        iconleft: { default: '' },
        enabled: { default: true },
    },

    computed: {
        componentid: function() {
            return "id-" + this.label.toLowerCase().replace(/[^a-zA-Z0-9 \-_]/g, "").replace(/\s/g, "-");
        }
    },

}
</script>

<style>
div.select, select {
    width: 100%;
}
</style>
