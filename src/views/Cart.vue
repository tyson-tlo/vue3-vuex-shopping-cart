<template>
    <div>
        <h1>Your cart</h1>
        
        <CartItemCard
            v-for="item in items"
            :key="item.id"
            :item="item" />

        <CartSummaryPaymentCard />
    </div>
</template>

<script>
    import CartItemCard from '../components/cart/CartItemCard.vue'
    import CartSummaryPaymentCard from '../components/cart/CartSummaryPaymentCard.vue'

    export default {
        components: {
            CartItemCard, CartSummaryPaymentCard
        },
        computed: {
            items() {
                return this.$store.getters.cartItems
            }
        }
    }
</script>