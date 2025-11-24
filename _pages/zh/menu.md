---
title: 菜单
lang: zh
permalink: /zh/menu/
layout: menu
translations:
  en: /menu/
  zh: /zh/menu/
  ja: /ja/menu/
  fr: /fr/menu/
  ko: /ko/menu/
---
<div class="menu content w-80 md:w-3/4">
  <h1 class="uppercase text-2xl lg:text-3xl text-center m-6">拉面</h1>
    <div class="mb-4">
      <p class="text-align-center md:text-base">
        所有拉面都配有叉烧肉或肉味噌、木耳、溏心蛋、豆芽、上海青、葱丝。
      </p>
    </div>
    <p class="text-align-center md:text-base">不含防腐剂，汤底食材每日新鲜自制。</p>
     <!-- TEN HOUR PORK SOUP -->
    <div class="section">
      <div class="section-header">
        <h2 class="text-2xl lg:text-3xl mt-20 mb-2">十小时猪骨汤</h2>
        <p>默认搭配猪肉叉烧, Goma Goma 和 Spicy Goma 除外 (这两款搭配肉味增)。</p>
      </div>
      {% for item in site.data.menu-price.pork_soup %}
      {% assign key = item[0] %}
      {% assign value = item[1] %}
      <div class="menu-item">
        <h3 class="text-lg md:text-xl lg:text-2xl">{{ value.name }}</h3>
        <div>{{ site.data.menu-description.pork_soup[key].description[page.lang] }}</div>
        <div>{{ value.price }}</div>
      </div>
    {% endfor %}
    </div>
    <div class="spacer"></div>
     <!-- CHICKEN SOUP -->
    <div class="section">
      <div class="section-header">
          <h2 class="text-2xl lg:text-3xl mb-2">六小时鸡骨汤</h2>
          <div>默认搭配叉烧肉，可加 $2 更换为鸡肉</div>
      </div>
      {% for item in site.data.menu-price.chicken_soup %}
      {% assign key = item[0] %}
      {% assign value = item[1] %}
        <div class="menu-item">
          <h3 class="text-lg md:text-xl lg:text-2xl">{{ value.name }}</h3>
          <div>{{ site.data.menu-description.chicken_soup[key].description[page.lang] }}</div>
          <div>{{ value.price }}</div>
        </div>
      {% endfor %}
    </div>
    <div class="spacer"></div>
      <!-- HOUSE SPECIAL -->
    <div class="section">
      <div class="section-header">
        <h2 class="uppercase text-2xl lg:text-3xl">素食 & 限定</h2>
      </div>
      {% for item in site.data.menu-price.house_special %}
      {% assign key = item[0] %}
      {% assign value = item[1] %}
      <div class="menu-item">
        <h3 class="text-lg md:text-xl lg:text-2xl">{{ value.name }}</h3>
        <div>
          {% if key == "feature_ramen" %}
              限定拉面，请咨询服务员
          {% else %}
            {{ site.data.menu-description.house_special[key].description[page.lang] }}
          {% endif %}
        </div>
        {% if value.price != "" %}
          <div>{{ value.price }}</div>
        {% endif %}
      </div>
    {% endfor %}
    </div>
    <div class="spacer"></div>
      <!-- EXTRA TOPPINGS -->
    <div class="section">
      <div class="section-header">
        <h2 class="uppercase text-2xl lg:text-3xl">加料选项</h2>
      </div>
      {% assign toppings = site.data.menu-price.extra_toppings %}
      {% assign toppings_desc = site.data.menu-description.extra_toppings %}
      {% for item in toppings %}
        {% assign key = item[0] %}
        {% assign topping = item[1] %}
        {% assign description_obj = toppings_desc[key] %}
        {% assign description = description_obj.description[page.lang] | default: topping.name %}
        <div class="menu-item">
          <h3 class="no-transform font-bold text-lg md:text-xl">
            {{ description }}
          </h3>
          <div>{{ topping.price }}</div>
        </div>
      {% endfor %}
    </div>
    <div class="spacer"></div>
      <!-- RICE BOWLS -->
    <div class="section">
      <div class="section-header">
        <h2 class="uppercase text-2xl lg:text-3xl mb-2">盖饭与小吃</h2>
        <div>搭配猪肉叉烧或鸡肉叉烧、豆芽、葱丝、以及自制照烧酱。</div>
      </div>
      {% for item in site.data.menu-price.rice_bowls %}
        {% assign key = item[0] %}
        {% assign value = item[1] %}
        <div class="menu-item">
          <h3 class="text-lg md:text-xl lg:text-2xl">{{ value.name }}</h3>
          <div>{{ site.data.menu-description.rice_bowls[key].description[page.lang] }}</div>
          <div>{{ value.price }}</div>
        </div>
      {% endfor %}
    </div>
    <div class="spacer"></div>
     <!-- BEVERAGES -->
    <div class="section">
      <div class="section-header">
        <h2 class="uppercase text-2xl lg:text-3xl">饮品</h2>
      </div>
    {% assign beverages = site.data.menu-price.beverages %}
    {% assign beverage_desc = site.data.menu-description.beverages %}
    {% for item in beverages %}
      {% assign key = item[0] %}
      {% assign value = item[1] %}
      {% if key == "soft_drink" %}
        {% assign soft_drinks = value %}
        {% assign soft_drinks_desc = beverage_desc.soft_drink %}
        {% for soft_item in soft_drinks %}
          {% assign soft_key = soft_item[0] %}
          {% assign soft_value = soft_item[1] %}
          <div class="menu-item">
            <h3 class="text-lg md:text-xl lg:text-2xl">{{ soft_value.name }}</h3>
            <div>{{ soft_drinks_desc[soft_key].description[page.lang] }}</div>
            <div>{{ soft_value.price }}</div>
          </div>
        {% endfor %}
      {% else %}
        <div class="menu-item">
          <h3 class="text-lg md:text-xl lg:text-2xl">{{ value.name }}</h3>
          <div>{{ beverage_desc[key].description[page.lang] }}</div>
          <div>{{ value.price }}</div>
        </div>
      {% endif %}
    {% endfor %}
    </div>
    <div class="spacer"></div>
    <div class="mb-6">
      <p class="text-align-center md:text-md lg:text-lg">本店不使用花生，如有其他过敏源请向服务员咨询。</p>
    </div>
    <p class="text-align-center md:text-md lg:text-lg">6人或以上将自动收取 18% 服务费，账单不可拆分。</p>
    <div class="uppercase font-semibold text-xl md:text-2xl mt-10">仅接受现金或借记卡付款！</div>
</div>