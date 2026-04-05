---
layout: page
title: All Posts
permalink: /posts/
section: shared
description: "Every post from JuicyForgJF and AmazonBBQ — research notes, write-ups, and things worth sharing."
nav: false
---

<div data-section="shared" style="max-width:860px;margin:0 auto;padding:0 8px;">

<h1 style="font-size:2rem;font-weight:800;color:#023E8A;margin-bottom:6px;">📝 All Posts</h1>
<p style="color:#5a7a8a;margin-bottom:36px;">Everything from both of us — newest first.</p>

<div style="display:flex;gap:10px;flex-wrap:wrap;margin-bottom:28px;align-items:center;">
  <span style="font-size:0.8rem;color:#7a9ab0;font-weight:600;text-transform:uppercase;letter-spacing:1px;">Filter:</span>
  <a href="#all" onclick="filterPosts('all',this)" class="filter-pill active" style="padding:5px 16px;border-radius:20px;font-size:0.8rem;font-weight:700;cursor:pointer;text-decoration:none;background:#023E8A;color:#fff;border:2px solid #023E8A;transition:all 0.2s;">All</a>
  <a href="#jf"  onclick="filterPosts('jf',this)"  class="filter-pill"        style="padding:5px 16px;border-radius:20px;font-size:0.8rem;font-weight:700;cursor:pointer;text-decoration:none;background:rgba(6,214,160,0.1);color:#028A6E;border:2px solid #06D6A0;transition:all 0.2s;">🐟 JuicyForgJF</a>
  <a href="#bbq" onclick="filterPosts('bbq',this)" class="filter-pill"        style="padding:5px 16px;border-radius:20px;font-size:0.8rem;font-weight:700;cursor:pointer;text-decoration:none;background:rgba(255,159,28,0.1);color:#C47800;border:2px solid #FF9F1C;transition:all 0.2s;">🔥 AmazonBBQ</a>
</div>

<div id="post-list" style="display:flex;flex-direction:column;gap:16px;">

{% assign all_posts = site.posts | sort: 'date' | reverse %}
{% for post in all_posts %}
  {% assign author_key = post.author | downcase %}
  {% if post.categories contains 'jf' %}
    {% assign author_key = 'jf' %}
    {% assign author_label = '🐟 JuicyForgJF' %}
    {% assign accent = '#06D6A0' %}
    {% assign accent_bg = 'rgba(6,214,160,0.08)' %}
    {% assign accent_dark = '#028A6E' %}
    {% assign pill_bg = 'rgba(6,214,160,0.15)' %}
  {% elsif post.categories contains 'bbq' %}
    {% assign author_key = 'bbq' %}
    {% assign author_label = '🔥 AmazonBBQ' %}
    {% assign accent = '#FF9F1C' %}
    {% assign accent_bg = 'rgba(255,159,28,0.08)' %}
    {% assign accent_dark = '#C47800' %}
    {% assign pill_bg = 'rgba(255,159,28,0.15)' %}
  {% else %}
    {% assign author_key = 'shared' %}
    {% assign author_label = '🤝 Shared' %}
    {% assign accent = '#0096C7' %}
    {% assign accent_bg = 'rgba(0,150,199,0.08)' %}
    {% assign accent_dark = '#023E8A' %}
    {% assign pill_bg = 'rgba(0,150,199,0.15)' %}
  {% endif %}

  <a href="{{ post.url | relative_url }}" class="post-card" data-author="{{ author_key }}"
     style="text-decoration:none;color:inherit;display:block;border-left:4px solid {{ accent }};padding:20px 24px;background:{{ accent_bg }};border-radius:0 14px 14px 0;transition:all 0.2s ease;"
     onmouseover="this.style.transform='translateX(4px)';this.style.boxShadow='0 4px 20px rgba(0,0,0,0.08)'"
     onmouseout="this.style.transform='';this.style.boxShadow=''">

    <div style="display:flex;justify-content:space-between;align-items:flex-start;flex-wrap:wrap;gap:8px;margin-bottom:8px;">
      <div style="display:flex;align-items:center;gap:10px;flex-wrap:wrap;">
        <span style="background:{{ accent }};color:#fff;padding:3px 12px;border-radius:12px;font-size:0.72rem;font-weight:700;">{{ author_label }}</span>
        <h3 style="margin:0;color:#023E8A;font-size:1rem;font-weight:700;line-height:1.3;">{{ post.title }}</h3>
      </div>
      <span style="color:#7a9ab0;font-size:0.8rem;white-space:nowrap;flex-shrink:0;">{{ post.date | date: "%b %-d, %Y" }}</span>
    </div>

    {% if post.description %}
    <p style="margin:0 0 10px;color:#3a5a6a;font-size:0.88rem;line-height:1.6;">{{ post.description }}</p>
    {% endif %}

    {% if post.tags %}
    <div style="display:flex;gap:6px;flex-wrap:wrap;">
      {% for tag in post.tags %}
        {% unless tag == 'jf' or tag == 'bbq' %}
        <span style="background:{{ pill_bg }};color:{{ accent_dark }};padding:2px 10px;border-radius:12px;font-size:0.7rem;font-weight:600;">{{ tag }}</span>
        {% endunless %}
      {% endfor %}
    </div>
    {% endif %}

    <div style="margin-top:10px;color:{{ accent_dark }};font-size:0.82rem;font-weight:600;">Read post →</div>
  </a>
{% endfor %}

</div><!-- /#post-list -->

</div>

<script>
function filterPosts(author, el) {
  // Update pill styles
  document.querySelectorAll('.filter-pill').forEach(function(p) {
    p.style.background = p.dataset.defaultBg || p.style.background;
    p.classList.remove('active');
  });

  // Show/hide cards
  document.querySelectorAll('.post-card').forEach(function(card) {
    if (author === 'all' || card.dataset.author === author) {
      card.style.display = 'block';
    } else {
      card.style.display = 'none';
    }
  });

  // Style active pill
  if (author === 'all') {
    el.style.background = '#023E8A';
    el.style.color = '#fff';
    el.style.borderColor = '#023E8A';
  } else if (author === 'jf') {
    el.style.background = '#06D6A0';
    el.style.color = '#fff';
    el.style.borderColor = '#06D6A0';
  } else {
    el.style.background = '#FF9F1C';
    el.style.color = '#fff';
    el.style.borderColor = '#FF9F1C';
  }

  return false;
}
</script>
