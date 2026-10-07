// ========================================
// PRODUCT DATA
// ========================================

const products = [
    {
        id: 1,
        name: "Rice (Plain)",
        price: 15.00,
        image: "images/rice.jfif"
    },
    {
        id: 2,
        name: "Fried Chicken (1 pc)",
        price: 65.00,
        image: "images/fried chicken.jfif"
    },
    {
        id: 3,
        name: "Pork Adobo",
        price: 60.00,
        image: "images/Pork Adobo.jfif"
    },
    {
        id: 4,
        name: "Vegetable Side Dish",
        price: 35.00,
        image: "images/Vegetables.jfif"
    },
    {
        id: 5,
        name: "Iced Tea (cup)",
        price: 20.00,
        image: "images/Ice Tea.jfif"
    },
    {
        id: 6,
        name: "Bottled Water",
        price: 20.00,
        image: "images/Mineral Water.jfif"
    }
];


// ========================================
// APPLICATION DATA
// ========================================

let cart = [];

let transactionNumber = 1;


// ========================================
// GET HTML ELEMENTS
// ========================================

const orderScreen =
    document.getElementById("order-screen");

const paymentScreen =
    document.getElementById("payment-screen");

const receiptScreen =
    document.getElementById("receipt-screen");

const productList =
    document.getElementById("product-list");

const cartItems =
    document.getElementById("cart-items");

const itemCount =
    document.getElementById("item-count");

const totalAmount =
    document.getElementById("total-amount");

const paymentTotal =
    document.getElementById("payment-total");

const cashInput =
    document.getElementById("cash-input");

const paymentMessage =
    document.getElementById("payment-message");

const receipt =
    document.getElementById("receipt");


// ========================================
// DISPLAY PRODUCTS
// ========================================

function displayProducts() {

    productList.innerHTML = "";

    products.forEach(product => {

        const productCard =
            document.createElement("div");

        productCard.className = "product-card";

        productCard.innerHTML = `
            <img class="product-image" src="${product.image}" alt="${product.name}">

            <div class="product-name">
                ${product.name}
            </div>

            <div class="product-price">
                ₱${product.price.toFixed(2)}
            </div>

            <button
                class="add-button"
                onclick="addToCart(${product.id})">

                ADD TO CART

            </button>
        `;

        productList.appendChild(productCard);
    });
}


// ========================================
// ADD TO CART
// ========================================

function addToCart(productId) {

    const product =
        products.find(
            product => product.id === productId
        );

    const existingItem =
        cart.find(
            item => item.id === productId
        );


    if (existingItem) {

        existingItem.quantity++;

    } else {

        cart.push({
            id: product.id,
            name: product.name,
            price: product.price,
            quantity: 1
        });
    }


    displayCart();
}


// ========================================
// DISPLAY CART
// ========================================

function displayCart() {

    if (cart.length === 0) {

        cartItems.innerHTML = `
            <div class="empty-cart">

                <div class="empty-icon">
                    🛒
                </div>

                <p>No items in the order</p>

                <span>
                    Add products from the left.
                </span>

            </div>
        `;

        itemCount.textContent = "0 items";

    } else {

        cartItems.innerHTML = "";

        let totalQuantity = 0;


        cart.forEach(item => {

            totalQuantity += item.quantity;


            const subtotal =
                item.price * item.quantity;


            const cartItem =
                document.createElement("div");

            cartItem.className = "cart-item";


            cartItem.innerHTML = `

                <div class="cart-item-top">

                    <span class="cart-item-name">
                        ${item.name}
                    </span>

                    <span class="cart-subtotal">
                        ₱${subtotal.toFixed(2)}
                    </span>

                </div>


                <div class="cart-controls">

                    <button
                        class="quantity-button"
                        onclick="decreaseQuantity(${item.id})">

                        −

                    </button>


                    <span class="quantity">
                        ${item.quantity}
                    </span>


                    <button
                        class="quantity-button"
                        onclick="increaseQuantity(${item.id})">

                        +

                    </button>


                    <button
                        class="remove-button"
                        onclick="removeFromCart(${item.id})">

                        REMOVE

                    </button>

                </div>
            `;


            cartItems.appendChild(cartItem);

        });


        itemCount.textContent =
            `${totalQuantity} item${totalQuantity !== 1 ? "s" : ""}`;
    }


    updateTotal();
}


// ========================================
// INCREASE QUANTITY
// ========================================

function increaseQuantity(productId) {

    const item =
        cart.find(
            item => item.id === productId
        );

    if (item) {
        item.quantity++;
    }

    displayCart();
}


// ========================================
// DECREASE QUANTITY
// ========================================

function decreaseQuantity(productId) {

    const item =
        cart.find(
            item => item.id === productId
        );


    if (item) {

        item.quantity--;


        if (item.quantity <= 0) {

            removeFromCart(productId);

            return;
        }
    }


    displayCart();
}


// ========================================
// REMOVE ITEM
// ========================================

function removeFromCart(productId) {

    cart =
        cart.filter(
            item => item.id !== productId
        );

    displayCart();
}


// ========================================
// CALCULATE TOTAL
// ========================================

function calculateTotal() {

    return cart.reduce(
        (total, item) => {

            return total +
                (item.price * item.quantity);

        },
        0
    );
}


// ========================================
// UPDATE TOTAL
// ========================================

function updateTotal() {

    const total =
        calculateTotal();


    totalAmount.textContent =
        `₱${total.toFixed(2)}`;

    paymentTotal.textContent =
        `₱${total.toFixed(2)}`;
}


// ========================================
// GO TO PAYMENT SCREEN
// ========================================

document
    .getElementById("proceed-button")
    .addEventListener(
        "click",
        goToPayment
    );


function goToPayment() {

    if (cart.length === 0) {

        alert(
            "Please add at least one product before proceeding to payment."
        );

        return;
    }


    paymentTotal.textContent =
        `₱${calculateTotal().toFixed(2)}`;


    paymentMessage.textContent = "";

    cashInput.value = "";


    orderScreen.classList.add("hidden");

    paymentScreen.classList.remove("hidden");

    cashInput.focus();
}


// ========================================
// BACK TO ORDER
// ========================================

document
    .getElementById("back-button")
    .addEventListener(
        "click",
        goBackToOrder
    );


function goBackToOrder() {

    paymentScreen.classList.add("hidden");

    orderScreen.classList.remove("hidden");

    paymentMessage.textContent = "";
}


// ========================================
// CONFIRM PAYMENT
// ========================================

document
    .getElementById("confirm-payment-button")
    .addEventListener(
        "click",
        processPayment
    );


function processPayment() {

    const total =
        calculateTotal();


    const cash =
        parseFloat(cashInput.value);


    // ==============================
    // VALIDATE PAYMENT
    // ==============================

    if (
        cashInput.value.trim() === "" ||
        isNaN(cash) ||
        cash < 0
    ) {

        paymentMessage.textContent =
            "Please enter a valid payment amount.";

        paymentMessage.style.color =
            "#c0392b";

        return;
    }


    // ==============================
    // CHECK INSUFFICIENT PAYMENT
    // ==============================

    if (cash < total) {

        paymentMessage.textContent =
            `Insufficient payment. Please enter at least ₱${total.toFixed(2)}.`;

        paymentMessage.style.color =
            "#c0392b";

        return;
    }


    // ==============================
    // CALCULATE CHANGE
    // ==============================

    const change =
        cash - total;


    // ==============================
    // GENERATE RECEIPT
    // ==============================

    generateReceipt(
        cash,
        change
    );
}


// ========================================
// GENERATE TRANSACTION NUMBER
// ========================================

function getTransactionNumber() {

    return `TXN-${String(transactionNumber).padStart(4, "0")}`;
}


// ========================================
// GENERATE RECEIPT
// ========================================

function generateReceipt(
    cash,
    change
) {

    const transactionId =
        getTransactionNumber();


    const total =
        calculateTotal();


    let receiptItems = "";


    cart.forEach(item => {

        const subtotal =
            item.price * item.quantity;


        receiptItems += `

            <div class="receipt-line">

                <span>
                    ${item.name} × ${item.quantity}
                </span>

                <span>
                    ₱${subtotal.toFixed(2)}
                </span>

            </div>

        `;
    });


    receipt.innerHTML = `

        <div class="success-message">
            ✓ PAYMENT SUCCESSFUL
        </div>


        <div class="receipt-header">

            <h3>
                Campus Cafeteria
            </h3>

            <p>
                Digital Receipt
            </p>

            <p>
                Transaction:
                ${transactionId}
            </p>

        </div>


        <div class="receipt-divider"></div>


        ${receiptItems}


        <div class="receipt-divider"></div>


        <div class="receipt-total">

            <span>
                Total
            </span>

            <span>
                ₱${total.toFixed(2)}
            </span>

        </div>


        <div class="receipt-line">

            <span>
                Amount Paid
            </span>

            <span>
                ₱${cash.toFixed(2)}
            </span>

        </div>


        <div class="receipt-line">

            <span>
                Change
            </span>

            <span>
                ₱${change.toFixed(2)}
            </span>

        </div>


        <div class="receipt-divider"></div>


        <div style="text-align: center;">

            Thank you for your order!

        </div>
    `;


    transactionNumber++;


    paymentScreen.classList.add("hidden");

    receiptScreen.classList.remove("hidden");
}


// ========================================
// CLEAR ORDER
// ========================================

document
    .getElementById("clear-order-button")
    .addEventListener(
        "click",
        clearOrder
    );


function clearOrder() {

    cart = [];

    cashInput.value = "";

    paymentMessage.textContent = "";

    receipt.innerHTML = "";


    paymentScreen.classList.add("hidden");

    receiptScreen.classList.add("hidden");

    orderScreen.classList.remove("hidden");


    displayCart();
}


// ========================================
// NEW TRANSACTION
// ========================================

document
    .getElementById("new-transaction-button")
    .addEventListener(
        "click",
        clearOrder
    );


// ========================================
// START APPLICATION
// ========================================

displayProducts();

displayCart();
