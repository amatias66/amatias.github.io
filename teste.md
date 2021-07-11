---
layout: default
title: amatias site de materiais
---

<style>
  .card-img-top {
width: 100%;
height: 40vh;
object-fit: cover;
}
</style>

{% include carousel.html %}




<div class="container home-page-news noselect ">

  <h2 class="">Última Notícia <span class="badge badge-secondary">News</span></h2>
  <br>
  {% for post in site.posts limit:1 %}
  <div class="row featurette shadow-lg p-3 mb-5 bg-white rounded ">
    <div class="col-md-7">
      <a id="url" href="{{ post.url }}" title="{{ post.title }}">
        <h2 id="title" class="featurette-heading">{{ post.title }} <span id="descricao" class="text-secondary">{{ post.description }}</span></h2>
      </a>
      <p id="excert" class="card-text"> {{ post.excerpt | strip_html | strip_newlines | truncate: 156 }} </p>

      <p class="card-text">
      <p class="noselect"> {% include read_time.html content=post.content %} </p>
      <footer class="blockquote-footer"> {% if post.author %} {{ post.author }} {% else %} {{ site.author }}
        {% endif %} <cite title="Source Title"> {{ post.date | date_to_string }} </cite></footer>

      </p>

      <a id="share" onclick="sharePost(`{{ post.title }}` , `{{  post.description }}` , `{{ post.url }}` )" class="text-muted share btn"><svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-share-fill texte-muted" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" d="M11 2.5a2.5 2.5 0 1 1 .603 1.628l-6.718 3.12a2.499 2.499 0 0 1 0 1.504l6.718 3.12a2.5 2.5 0 1 1-.488.876l-6.718-3.12a2.5 2.5 0 1 1 0-3.256l6.718-3.12A2.5 2.5 0 0 1 11 2.5z" />
        </svg></a>
      <p class="result" hidden></p>

      {% for tag in post.tags %}
      {% capture tag_name %}{{ tag }}{% endcapture %}

      <a href="/tag/{{ tag_name }}"><code class="noselect  btn btn-light btn-sm mb-1 text-small mt-2 font-weight-light text-secondary">
          <nobr>
            <svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-hash" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path d="M8.39 12.648a1.32 1.32 0 0 0-.015.18c0 .305.21.508.5.508.266 0 .492-.172.555-.477l.554-2.703h1.204c.421 0 .617-.234.617-.547 0-.312-.188-.53-.617-.53h-.985l.516-2.524h1.265c.43 0 .618-.227.618-.547 0-.313-.188-.524-.618-.524h-1.046l.476-2.304a1.06 1.06 0 0 0 .016-.164.51.51 0 0 0-.516-.516.54.54 0 0 0-.539.43l-.523 2.554H7.617l.477-2.304c.008-.04.015-.118.015-.164a.512.512 0 0 0-.523-.516.539.539 0 0 0-.531.43L6.53 5.484H5.414c-.43 0-.617.22-.617.532 0 .312.187.539.617.539h.906l-.515 2.523H4.609c-.421 0-.609.219-.609.531 0 .313.188.547.61.547h.976l-.516 2.492c-.008.04-.015.125-.015.18 0 .305.21.508.5.508.265 0 .492-.172.554-.477l.555-2.703h2.242l-.515 2.492zm-1-6.109h2.266l-.515 2.563H6.859l.532-2.563z" />
            </svg>

            {{ tag_name }}

          </nobr>
        </code>&nbsp;</a>
      {% endfor %}

    </div>
    {% if post.featured-image And post.featured-image != "" And post.featured-image != nil    %}

    <!--"imageValidate(`{{ post.featured-image }}`)" ==true-->

    <div class="col-md-5 float-left  ">
      <img alt="noticia-principal1" class="featurette-image img-fluid mx-auto pull-left lazyload  " src="{{ post.featured-image }}" data-src="{{ post.featured-image }}" data-holder-rendered="true" style="width:50%; ">
    </div>
    {% endif %}

  </div>
  {% endfor %}
</div>



<section class="more-services section-bg noselect">
  <div class="container">

    <h3 class=" text-center ">Notícias Recentes <span class="badge badge-secondary"><svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-newspaper " fill="currentColor" xmlns="http://www.w3.org/2000/svg">
          <path fill-rule="evenodd" d="M0 2.5A1.5 1.5 0 0 1 1.5 1h11A1.5 1.5 0 0 1 14 2.5v10.528c0 .3-.05.654-.238.972h.738a.5.5 0 0 0 .5-.5v-9a.5.5 0 0 1 1 0v9a1.5 1.5 0 0 1-1.5 1.5H1.497A1.497 1.497 0 0 1 0 13.5v-11zM12 14c.37 0 .654-.211.853-.441.092-.106.147-.279.147-.531V2.5a.5.5 0 0 0-.5-.5h-11a.5.5 0 0 0-.5.5v11c0 .278.223.5.497.5H12z" />
          <path d="M2 3h10v2H2V3zm0 3h4v3H2V6zm0 4h4v1H2v-1zm0 2h4v1H2v-1zm5-6h2v1H7V6zm3 0h2v1h-2V6zM7 8h2v1H7V8zm3 0h2v1h-2V8zm-3 2h2v1H7v-1zm3 0h2v1h-2v-1zm-3 2h2v1H7v-1zm3 0h2v1h-2v-1z" />
        </svg></span></h3>

    <div class="row justify-content-center">
  
      {% for post in site.posts offset:1 limit:3 %}
      <div class="col-lg-4 col-md-6 d-flex align-items-stretch mb-5 mb-lg-0">
     
        <div class="card">
          {% if post.featured-image And post.featured-image != "" And post.featured-image != nil    %}
          <div class="image">
          <img src="{{ post.featured-image }}" data-src="{{ post.featured-image }}" data-holder-rendered="true" onError="this.onerror=null;this.src='https://gdrverderena.pt/assets/img/more-service-3.jpg';" draggable="false" class="card-img-top" alt="...">
          </div>
          {% endif %}
          <div class="card-body">

            <h5 class="card-title"><a href="{{ post.url }}">{{ post.title }}</a></h5>
            <p class="card-text">{{ post.description }}</p>
            <p id="excert" class="card-text"> {{ post.excerpt | strip_html | strip_newlines | truncate: 96 }} </p>

            <a href="{{ post.url }}" class="btn">Ver Notícia</a>
          </div>
          <div class="card-footer text-muted">
            <a id="share" onclick="sharePost(`{{ post.title }}` , `{{  post.description }}` , `{{ post.url }}` )" class="text-muted share btn"><svg width="1em" height="1em" viewBox="0 0 16 16" class="bi bi-share-fill texte-muted" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" d="M11 2.5a2.5 2.5 0 1 1 .603 1.628l-6.718 3.12a2.499 2.499 0 0 1 0 1.504l6.718 3.12a2.5 2.5 0 1 1-.488.876l-6.718-3.12a2.5 2.5 0 1 1 0-3.256l6.718-3.12A2.5 2.5 0 0 1 11 2.5z" />
              </svg></a>
            <p class="result" hidden></p>
          </div>
        </div>
      </div>
      {% endfor %}
  
    </div>

  </div>
</section>

<br>


<br>

{% include partners.html %}
