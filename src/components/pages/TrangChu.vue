<template>
    <div id="products" v-if="currentPage === 'products'">
        <div class="banner">
            <p>Tanisha</p>
            <a>Ngon khó cưỡng!!</a>
        </div>

        <div class="container products my-3">
            <div class="tieude">
                <h1>Sale</h1>
                
            </div>
            <div class="product-items">
                <div class="product-item" v-for="product in products" :key="product.id">
                    <img :src="require(`@/assets/pic/${product.thum}`)" alt="" style="width: 95%;" >
                    <h3>{{ product.name }}</h3>
                    <p style="text-align:left; color:red;margin:3px;"><del>Giá cũ: {{ product.oldprice }}<sup>đ</sup>  </del></p>
                    <p style="text-align:left"><span >Giá mới: {{ product.price }}</span><sup>đ</sup></p>
                    <button @click="$emit('addToCart', product)" >Thêm vào giỏ hàng</button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default{
    name:'TrangChu',
    props:['product'],
    data(){
        return{
            currentPage: 'products',
            products:[
                { id: 1,category:"banhkem", name: 'Bánh Kem Dâu',  thum:  'kd.jpg', oldprice:"300.000", price: "200.000" },
                { id: 2,category:"banhkem", name: 'Bánh Kem Socola', thum:  'ks.webp', oldprice:"350.000", price: "250.000" },
                { id: 8, category:"banhlava", name: 'Bánh Lava Socola',  thum: 'scllv.png'  , oldprice:"400.000", price: "350.000" },
                { id: 9, category:"banhlava", name: 'Bánh Lava Matcha', thum: 'mclv.jpg'  , oldprice:"500.000" ,price: "400.000" },
                { id: 16, category:"banhtỉamisu", name: 'Tiramisu Trái Cây',  thum:  'traicay.jpg', oldprice:"700.000", price: "480.000" },
                { id: 17, category:"banhtỉamisu", name: 'Tiramisu Cafe',   thum:  'caphe.jpg', oldprice:"600.000", price: "470.000" },
        ]
        }
    },
    methods:{
        addToCart(shop) {
            this.$emit('addToCart', shop);
            alert(`${shop.name} đã được thêm vào giỏ hàng!`);
        }
    },

}
</script>
<style>
.products{
    border: 1px solid #EFF0F3;
    border-radius: 5px;
    
}
.tieude{
    display: flex;
    color: #FF5622;
}



.banner p{
font-size: 100px;
text-align: center;
padding-top:50px ;
}
.banner{
        background-image: url('./src/assets/pic/banner.jpg');
        background-size: cover; /* Điều chỉnh ảnh để vừa khít */
        background-position: center; /* Căn giữa ảnh nền */
        background-repeat: no-repeat; /* Không lặp lại ảnh */
        padding: 200px;
}
.product-items {
    display: flex;
    justify-content: space-between;
    padding: 12px;
    flex-wrap: wrap;
}
.product-item {
border:10px #FF5622;
    background-color: #fff;
    padding: 12px;
    margin-bottom: 12px;
    text-align: center;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
}

.product-item img {
    width: 100%;
    height: 50%;
    margin-bottom: 20px;
    object-fit: cover;
} 
.product-item button {
    margin-bottom: 12px;
    height: 30px;
    padding: 0 12px;
    cursor: pointer;
    border: none;
    border-radius: 5px;
}
.product-item-text p{
    padding:0px;
    margin: 2px;
}
.product-item button:hover {
    background-color: greenyellow;
    transform: translateY(-5px);
    box-shadow: 0px 5px 10px rgba(90, 151, 0, 0.908);
}
.btn-added {
    background-color: gray;
    color: white;
    border: none;
    cursor: not-allowed;
}
</style>