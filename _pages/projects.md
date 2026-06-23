---
layout: page
title: projects
permalink: /projects/
description: Research projects I'm currently working on.
nav: true
nav_order: 3
display_categories: [research]
---

<!-- pages/projects.md -->
<div class="projects publications">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate a publication-style row for each project -->
  <ol class="bibliography">
    {% for project in sorted_projects %}
    <li>
      <div class="title">{{ project.title }}</div>
      {%- assign self_name = site.first_name | append: ' ' | append: site.last_name -%}
      {%- assign all_authors = project.authors -%}
      {%- if project.more_authors -%}{%- assign all_authors = project.authors | concat: project.more_authors -%}{%- endif -%}
      <div class="author" data-self="{{ self_name }}" data-authors='{{ all_authors | jsonify }}' data-primary-count="{{ project.authors.size }}">{%- assign primary_count = project.authors.size -%}{%- for author in all_authors -%}{% unless forloop.first %}{% if forloop.last %}{% if all_authors.size > 2 %}, and {% else %} and {% endif %}{% else %}, {% endif %}{% endunless %}{% assign idx = forloop.index0 %}{% if author == self_name %}<em>{{ author }}</em>{% elsif idx >= primary_count %}<span class="author-secondary" style="color: var(--global-text-color-light); border-bottom: 1px dashed var(--global-text-color-light);">{{ author }}</span>{% else %}{{ author }}{% endif %}{%- endfor -%}</div>
      <div class="periodical">
        <span style="color: var(--global-theme-color);">{{ project.group }}</span>{% if project.period %}, {{ project.period }}{% endif %}
      </div>
      {% if project.description %}
        <div class="periodical" style="color: var(--global-text-color-light); font-style: italic;">{{ project.description }}</div>
      {% endif %}
      <div class="links">
        {% if project.website %}
          <a href="{{ project.website }}" class="btn btn-sm z-depth-0" role="button">Website</a>
        {% else %}
          <a href="{{ project.url | relative_url }}" class="btn btn-sm z-depth-0" role="button">Website</a>
        {% endif %}
        {% if project.pdf %}
          {% if project.pdf contains '://' %}
            <a href="{{ project.pdf }}" class="btn btn-sm z-depth-0" role="button">PDF</a>
          {% else %}
            <a href="{{ project.pdf | prepend: '/assets/pdf/' | relative_url }}" class="btn btn-sm z-depth-0" role="button">PDF</a>
          {% endif %}
        {% endif %}
        {% if project.code %}
          <a href="{{ project.code }}" class="btn btn-sm z-depth-0" role="button">Code</a>
        {% endif %}
      </div>
    </li>
    {% endfor %}
  </ol>
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate a publication-style row for each project -->
  <ol class="bibliography">
    {% for project in sorted_projects %}
    <li>
      <div class="title">{{ project.title }}</div>
      {%- assign self_name = site.first_name | append: ' ' | append: site.last_name -%}
      {%- assign all_authors = project.authors -%}
      {%- if project.more_authors -%}{%- assign all_authors = project.authors | concat: project.more_authors -%}{%- endif -%}
      <div class="author" data-self="{{ self_name }}" data-authors='{{ all_authors | jsonify }}' data-primary-count="{{ project.authors.size }}">{%- assign primary_count = project.authors.size -%}{%- for author in all_authors -%}{% unless forloop.first %}{% if forloop.last %}{% if all_authors.size > 2 %}, and {% else %} and {% endif %}{% else %}, {% endif %}{% endunless %}{% assign idx = forloop.index0 %}{% if author == self_name %}<em>{{ author }}</em>{% elsif idx >= primary_count %}<span class="author-secondary" style="color: var(--global-text-color-light); border-bottom: 1px dashed var(--global-text-color-light);">{{ author }}</span>{% else %}{{ author }}{% endif %}{%- endfor -%}</div>
      <div class="periodical">
        <span style="color: var(--global-theme-color);">{{ project.group }}</span>{% if project.period %}, {{ project.period }}{% endif %}
      </div>
      {% if project.description %}
        <div class="periodical" style="color: var(--global-text-color-light); font-style: italic;">{{ project.description }}</div>
      {% endif %}
      <div class="links">
        {% if project.website %}
          <a href="{{ project.website }}" class="btn btn-sm z-depth-0" role="button">Website</a>
        {% else %}
          <a href="{{ project.url | relative_url }}" class="btn btn-sm z-depth-0" role="button">Website</a>
        {% endif %}
        {% if project.pdf %}
          {% if project.pdf contains '://' %}
            <a href="{{ project.pdf }}" class="btn btn-sm z-depth-0" role="button">PDF</a>
          {% else %}
            <a href="{{ project.pdf | prepend: '/assets/pdf/' | relative_url }}" class="btn btn-sm z-depth-0" role="button">PDF</a>
          {% endif %}
        {% endif %}
        {% if project.code %}
          <a href="{{ project.code }}" class="btn btn-sm z-depth-0" role="button">Code</a>
        {% endif %}
      </div>
    </li>
    {% endfor %}
  </ol>
{% endif %}
</div>

<script>
(function () {
  function authorsHTML(names, selfName, hiddenCount, primaryCount) {
    var n = names.length;
    var html = names
      .map(function (name, i) {
        var inner = name === selfName ? "<em>" + name + "</em>" : name;
        if (i >= primaryCount) {
          inner =
            '<span class="author-secondary" style="color: var(--global-text-color-light); border-bottom: 1px dashed var(--global-text-color-light);">' +
            inner +
            "</span>";
        }
        if (i === 0) return inner;
        if (i === n - 1 && hiddenCount === 0) {
          return (n > 2 ? ", and " : " and ") + inner;
        }
        return ", " + inner;
      })
      .join("");
    if (hiddenCount > 0) {
      var label = hiddenCount + " more author" + (hiddenCount > 1 ? "s" : "");
      html += (n > 0 ? ", and " : "") + '<span class="more-authors" role="button" tabindex="0">' + label + "</span>";
    }
    return html;
  }

  function expand(container, all, selfName, primaryCount) {
    container.dataset.expanded = "true";
    container.style.whiteSpace = "normal";
    container.style.overflow = "visible";
    container.innerHTML = authorsHTML(all, selfName, 0, primaryCount);
  }

  function fitAuthors(container) {
    if (container.dataset.expanded === "true") return;
    var all = JSON.parse(container.getAttribute("data-authors"));
    var selfName = container.getAttribute("data-self");
    var primaryCount = parseInt(container.getAttribute("data-primary-count"), 10) || all.length;
    container.style.whiteSpace = "nowrap";
    container.style.overflow = "hidden";
    for (var visible = all.length; visible >= 1; visible--) {
      var hidden = all.length - visible;
      container.innerHTML = authorsHTML(all.slice(0, visible), selfName, hidden, primaryCount);
      if (visible === 1 || container.scrollWidth <= container.clientWidth) break;
    }
    var moreEl = container.querySelector(".more-authors");
    if (moreEl) {
      var onActivate = function () {
        expand(container, all, selfName, primaryCount);
      };
      moreEl.addEventListener("click", onActivate);
      moreEl.addEventListener("keydown", function (e) {
        if (e.key === "Enter" || e.key === " ") {
          e.preventDefault();
          onActivate();
        }
      });
    }
  }

  function fitAll() {
    document.querySelectorAll(".projects .author[data-authors]").forEach(fitAuthors);
  }

  document.addEventListener("DOMContentLoaded", fitAll);

  var resizeTimer;
  window.addEventListener("resize", function () {
    clearTimeout(resizeTimer);
    resizeTimer = setTimeout(fitAll, 150);
  });
})();
</script>
