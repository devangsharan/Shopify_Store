# Shopify_Store

Modified Files

1.product-card.liquid

2.collection.liquid

3.index.liquid

4.cart.liquid

Implementations

Task 1: Dynamic Product Badge

File Modified: product-card.liquid

Added a "Budget Pick" badge for products under ₹500.

Added a "Limited Stock" badge for products with fewer than 5 items in stock.

Displayed both badges when both conditions are met.

{% if product.price < 500 %}
    <span class="badge">Budget Pick</span>
{% endif %}

{% if product.variants.first.inventory_quantity < 5 %}
    <span class="badge">Limited Stock</span>
{% endif %}

Task 2: Custom Collection Filter

File Modified: collection.liquid

Implemented a dropdown to filter products by tags (best-seller, new-arrival, discounted).

Ensured filtering does not affect pagination.

<select id="filter" onchange="filterProducts()">
    <option value="all">All Products</option>
    <option value="best-seller">Best Seller</option>
    <option value="new-arrival">New Arrival</option>
    <option value="discounted">Discounted</option>
</select>

{% for product in collection.products %}
    {% if product.tags contains selected_tag or selected_tag == 'all' %}
        <!-- Product display logic -->
    {% endif %}
{% endfor %}

Task 3: Personalized Greeting (Homepage Feature)

File Modified: index.liquid

Displayed a greeting based on the time of day:

"Good Morning, Shopper!" before 12 PM.

"Good Afternoon, Shopper!" between 12 PM – 6 PM.

"Good Evening, Shopper!" after 6 PM.

{% assign current_hour = "now" | date: "%H" %}

{% if current_hour < 12 %}
    <p>Good Morning, Shopper!</p>
{% elsif current_hour < 18 %}
    <p>Good Afternoon, Shopper!</p>
{% else %}
    <p>Good Evening, Shopper!</p>
{% endif %}

Task 4: Custom Upsell Section (Cart Page)

File Modified: cart.liquid

Suggested a product from the Accessories collection if the cart total is below ₹1000.

Suggested a product from the Premium collection if the cart total is ₹1000 or more.

{% assign cart_total = cart.total_price %}

{% if cart_total < 1000 %}
    {% assign upsell_product = collections['Accessories'].products.first %}
{% else %}
    {% assign upsell_product = collections['Premium'].products.first %}
{% endif %}

<p>Recommended for you: {{ upsell_product.title }}</p>

Bonus Task: Dynamic "Buy More, Save More" Message

File Modified: cart.liquid

Displayed "Spend ₹500 more to get free shipping!" if cart total is below ₹500.

Displayed "You’ve unlocked free shipping!" if cart total is ₹500 or above.

{% if cart_total < 500 %}
    <p>Spend ₹{{ 500 | minus: cart_total }} more to get free shipping!</p>
{% else %}
    <p>You’ve unlocked free shipping!</p>
{% endif %}

Submission Details

Modified Liquid files: product-card.liquid, collection.liquid, index.liquid, cart.liquid.

Shopify development store: dswebservices.

Prepared by: Devang Sharan
