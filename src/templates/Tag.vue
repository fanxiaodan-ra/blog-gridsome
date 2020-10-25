<template>
  <div>
    <Layout>
      <!-- Page Header -->
      <header class="masthead" style="background-image: url('/img/home-bg.jpg')">
        <div class="overlay"></div>
        <div class="container">
          <div class="row">
            <div class="col-lg-8 col-md-10 mx-auto">
              <div class="site-heading">
                <h1># {{$page.tag.title}}</h1>
                <span class="subheading">A Blog Theme by Start Bootstrap</span>
              </div>
            </div>
          </div>
        </div>
      </header>

      <!-- Main Content -->
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="post-preview" v-for="post in $page.tag.posts" :key="post.id">
              <g-link :to="'/post/' + post.id">
                <h2 class="post-title">
                 {{ post.title}}
                </h2>
              </g-link>
              <hr>
            </div>
          </div>
        </div>
      </div>
    </Layout>
  </div>
</template>
<page-query>
query($id: ID) {
  tag: strapiTag (id: $id) {
    title
    posts{
      id
      title
    }
  }
}
</page-query>