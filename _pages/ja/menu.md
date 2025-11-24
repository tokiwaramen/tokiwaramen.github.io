---
title: メニュー
lang: ja
permalink: /menu/
layout: menu
translations:
  en: /menu/
  zh: /zh/menu/
  ja: /ja/menu/
  fr: /fr/menu/
  ko: /ko/menu/
---

<div class="menu content w-80 md:w-3/4">
  <h1 class="uppercase text-2xl lg:text-3xl text-center m-6">ラーメン</h1>
  <div class="mb-4">
    <p class="text-align-center md:text-base">
      ラーメン全種はチャーシューか肉味噌、木耳、半熟卵、萌やし、チンゲンサイとネギ付きです。
    </p>
  </div>
  <p class="text-align-center md:text-base">保存剤一切使いません。出汁は自家製で毎日新鮮。</p>
  
  <!-- TEN HOUR PORK SOUP -->
  <div class="section">
    <div class="section-header">
      <h2 class="text-2xl lg:text-3xl mt-20 mb-2">十時間煮詰めた豚出汁</h2>
      <p>ラー油かけ肉味噌と中辛ゴマダレ以外のラーメンがチャーシュー付きです。</p>

    </div>
    {% for item in site.data.menu-price.pork_soup %}
    {% assign key = item[0] %}
    {% assign value = item[1] %}
    <div class="menu-item">
      <h3>{{ value.name }}</h3>
      <div>{{ site.data.menu-description.pork_soup[key].description[page.lang] }}</div>
      <div>{{ value.price }}</div>
    </div>
  {% endfor %}
  </div>

  <div class="spacer"></div>

  <!-- CHICKEN SOUP -->
  <div class="section">
    <div class="section-header">
      <h2 class="text-2xl lg:text-3xl mb-2">六時間煮詰めた鶏出汁</h2>
      <div>チャーシュー付き。鶏肉と交換した場合、＄２チャージがかかります。</div>
    </div>
    {% for item in site.data.menu-price.chicken_soup %}
    {% assign key = item[0] %}
    {% assign value = item[1] %}
    <div class="menu-item">
      <h3>{{ value.name }}</h3>
      <div>{{ site.data.menu-description.chicken_soup[key].description[page.lang] }}</div>
      <div>{{ value.price }}</div>
    </div>
  {% endfor %}
  </div>

  <div class="spacer"></div>

  <!-- HOUSE SPECIAL -->
  <div class="section">
    <div class="section-header">
      <h2 class="uppercase text-2xl lg:text-3xl">自家製出汁</h2>
    </div>
    {% for item in site.data.menu-price.house_special %}
    {% assign key = item[0] %}
    {% assign value = item[1] %}
    <div class="menu-item">
      <h3>{{ value.name }}</h3>
      <div>
        {% if key == "feature_ramen" %}
          店員まで声を掛けてください。
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
    <h2 class="uppercase text-2xl lg:text-3xl">トッピング</h2>
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
      <h2 class="uppercase text-2xl lg:text-3xl mb-2">丼もの・おかず</h2>
      <div>豚か鶏肉、萌やし、ネギと自家製照り焼きソース付きです。</div>
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
      <h2 class="uppercase text-2xl lg:text-3xl">飲み物</h2>
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
    <p class="text-align-center md:text-md lg:text-lg">ピーナッツが当店の料理に含まれていません。アレルギーの心配があった場合に店員さんに声をかけてください。</p>
  </div>
  <p class="text-align-center md:text-md lg:text-lg">６人以上のグループは１８％の追加料金がかかります。山分けはできません。</p>
  <div class="uppercase font-semibold text-xl md:text-2xl mt-10">現金とデビットのみ</div>
</div>
