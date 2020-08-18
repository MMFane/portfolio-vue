<script>
    export default {
        name: "DynamicHeader",
        render: function (createElement) {
            return createElement(
                'h' + this.level,
                this.$slots.default
            )
        },
        props: {
            level: {
                type: Number,
                default: 2
            }
        }
    }
</script>