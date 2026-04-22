{%- style -%}
.rage-body {
background: #0a0a0a;
color: #fff;
font-family: Arial, sans-serif;
padding-bottom: 50px;
}
.rage-header {
background: black;
padding: 40px 20px;
text-align: center;
font-size: 40px;
font-weight: bold;
color: #ff1a1a;
text-transform: uppercase;
letter-spacing: 2px;
}
.rage-hero {
text-align: center;
padding: 60px 20px;
}
.rage-grid {
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
gap: 30px;
padding: 20px;
max-width: 1200px;
margin: 0 auto;
}
.rage-product-card {
background: #1a1a1a;
padding: 20px;
border-radius: 4px;
text-align: center;
transition: transform 0.2s;
border: 1px solid #333;
}
.rage-product-card:hover {
border-color: #ff1a1a;
}
.rage-product-card img {
width: 100%;
height: auto;
margin-bottom: 15px;
}
.rage-btn {
background: #ff1a1a;
padding: 12px 24px;
color: #000;
font-weight: bold;
cursor: pointer;
border: none;
width: 100%;
text-transform: uppercase;
margin-top: 15px;
}
.rage-btn:hover {
background: #cc0000;
}
{%- endstyle -%}

<div class="rage-body">
<header class="rage-header">
{{ section.settings.heading | upcase }}
</header>

<section class="rage-hero">
<h1>{{ section.settings.hero_title }}</h1>
<p>{{ section.settings.hero_subtitle }}</p>
</section>

<div class="rage-grid">
{% for product in section.settings.collection.products %}
<div class="rage-product-card">
{% if product.featured_image %}
<img src="{{ product.featured_image | img_url: '400x400', crop: 'center' }}" alt="{{ product.title }}">
{% endif %}
<h3>{{ product.title }}</h3>
<p>{{ product.price | money }}</p>

{% comment %} Using Shopify's native form for actual sales {% endcomment %}
{% form 'product', product %}
<input type="hidden" name="id" value="{{ product.selected_or_first_available_variant.id }}">
<button type="submit" class="rage-btn">Add to Cart</button>
{% endform %}
</div>
{% endfor %}
</div>
</div>

{% schema %}
{
"name": "Rage District Shop",
"settings": [
{
"type": "text",
"id": "heading",
"label": "Store Name",
"default": "Rage District"
},
{
"type": "text",
"id": "hero_title",
"label": "Hero Title",
"default": "Streetwear Built From Chaos"
},
{
"type": "text",
"id": "hero_subtitle",
"label": "Hero Subtitle",
"default": "Rage District Collection"
},
{
"type": "collection",
"id": "collection",
"label": "Select Collection"
}
],
"presets": [
{
"name": "Rage District Shop"
}
]
}
{% endschema %}
