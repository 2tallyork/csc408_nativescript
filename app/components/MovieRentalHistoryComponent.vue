<template>
    <FlexboxLayout flexDirection="row" class="list-group-item">
        <GridLayout columns="3*,7*" rows="*,*,*,*" width="100%" >
            <Image :src="imageUrl" row="0" col="0" rowSpan="4"  class="thumbnail"/>

            <Label :text="this.rental.name"  class="label-text" />
            <Label :text="this.rental.email"  class="label-text" />
            <Label :text="'Rented: ' + rented"  class="label-text" />
            <Label :text="'Returned: ' + returned"  class="label-text" />
        </GridLayout>
    </FlexboxLayout>
</template>

<script>
    export default {
        data () {
            return {}
        },
        methods: {
        },
        computed: {
            imageUrl: function(){
                return "https://codeflare.tech/images/movie_" + this.rental.transaction.movie_id + ".jpg";
            },
            rented: function(){
                var options = { year: 'numeric', month: 'numeric', day: 'numeric'};
                var day  = new Date(this.rental.transaction.rent_date);
                return (day.getMonth() + 1) + '/' + day.getDate() + '/' +  day.getFullYear();
            },
            returned: function(){
                var options = {year: 'numeric', month: 'numeric', day: 'numeric'};
                var day  = new Date(this.rental.transaction.return_date);
                return (day.getMonth() + 1) + '/' + day.getDate() + '/' +  day.getFullYear();
            }
        },
        props: ['rental']
    }
</script>
