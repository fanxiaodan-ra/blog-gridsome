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
                <h1>Clean Blog</h1>
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
            <div class="post-preview" v-for="edge in $page.post.edges" :key="edge.node.id">
              <g-link :to="'/post/' + edge.node.id">
                <h2 class="post-title">
                 {{ edge.node.title}}
                </h2>
              </g-link>
              <p class="post-meta">Posted by
                <a href="#">{{edge.node.create_by.firstName + edge.node.create_by.lastName}}</a>
                on {{edge.node.created_at}}</p>
              <p>
                <span v-for="tag in edge.node.tags" :key="tag.id">
                  <g-link :to="'/tag/' + tag.id">{{ tag.title }}</g-link>
                </span>
              </p>
              <hr>
            </div>
            <!-- Pager -->
            <Pager :info="$page.post.pageInfo"/>
          </div>
        </div>
      </div>
    </Layout>


  </div>
</template>
<page-query>
query ($page: Int) {
  post: allStrapiPost (perPage: 2, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        created_at
        create_by {
          firstName
          lastName
        }
        tags {
          id
          title
        }
      }
    }
  }
}
</page-query>
<script>
import { Pager } from 'gridsome'
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  components: { Pager }
}
</script>

<style>
</style>
