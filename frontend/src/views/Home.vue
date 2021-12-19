<template>
  <div class="home">
    <h1 class="text-center mb-5">Home</h1>
    <article v-for="article in articles">
      <h3><router-link :to="`/article/${article.slug}`">{{article.title}}</router-link></h3>
      <div>
        {{article.description}}
        <router-link class="aa" :to="`/article/${article.slug}`"> + more</router-link>
      </div>
      <hr>
    </article>
  </div>
</template>
 
<script>
	export default {
	  name: 'Home',

    data() {

      let articles = localStorage.getItem("articles")
      articles = JSON.parse(articles)

      return {
        articles : articles
        // articles: [
        //   {
        //     title       : "Title 1",
        //     slug        : "title-1",
        //     description : "Lorem ipsum, dolor sit amet consectetur adipisicing, elit. Laboriosam ullam, quidem suscipit alias cum vitae cumque debitis repudiandae laudantium doloremque",
        //     content     : "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae, voluptas facilis! Eveniet blanditiis nulla sequi ut consectetur laudantium sit architecto, a quam repudiandae natus cupiditate, odio optio fugit, culpa sed modi accusamus cumque vero perspiciatis. Quam porro ut totam, odio vel architecto ex provident quo dolor fugit vitae, animi soluta voluptates illum labore magni aliquam quos tempora cum eligendi sit laborum odit atque. Qui fugiat nobis quae, neque nostrum reprehenderit accusamus voluptate, numquam aut unde aperiam obcaecati deleniti voluptatum debitis cum minima veritatis eius, incidunt sed soluta sint! Libero nihil quasi explicabo quos delectus, consectetur nemo soluta doloremque velit, mollitia.",
        //   },
        //   {
        //     title       : "Title 2",
        //     slug        : "title-2",
        //     description : "Lorem ipsum, dolor sit amet consectetur adipisicing, elit. Laboriosam ullam, quidem suscipit alias cum vitae cumque debitis repudiandae laudantium doloremque",
        //     content     : "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae, voluptas facilis! Eveniet blanditiis nulla sequi ut consectetur laudantium sit architecto, a quam repudiandae natus cupiditate, odio optio fugit, culpa sed modi accusamus cumque vero perspiciatis. Quam porro ut totam, odio vel architecto ex provident quo dolor fugit vitae, animi soluta voluptates illum labore magni aliquam quos tempora cum eligendi sit laborum odit atque. Qui fugiat nobis quae, neque nostrum reprehenderit accusamus voluptate, numquam aut unde aperiam obcaecati deleniti voluptatum debitis cum minima veritatis eius, incidunt sed soluta sint! Libero nihil quasi explicabo quos delectus, consectetur nemo soluta doloremque velit, mollitia.",
        //   }, 
        //   {
        //     title       : "Title 3",
        //     slug        : "title-3",
        //     description : "Lorem ipsum, dolor sit amet consectetur adipisicing, elit. Laboriosam ullam, quidem suscipit alias cum vitae cumque debitis repudiandae laudantium doloremque",
        //     content     : "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae, voluptas facilis! Eveniet blanditiis nulla sequi ut consectetur laudantium sit architecto, a quam repudiandae natus cupiditate, odio optio fugit, culpa sed modi accusamus cumque vero perspiciatis. Quam porro ut totam, odio vel architecto ex provident quo dolor fugit vitae, animi soluta voluptates illum labore magni aliquam quos tempora cum eligendi sit laborum odit atque. Qui fugiat nobis quae, neque nostrum reprehenderit accusamus voluptate, numquam aut unde aperiam obcaecati deleniti voluptatum debitis cum minima veritatis eius, incidunt sed soluta sint! Libero nihil quasi explicabo quos delectus, consectetur nemo soluta doloremque velit, mollitia.",
        //   },
        //   {
        //     title       : "Title 4",
        //     slug        : "title-4",
        //     description : "Lorem ipsum, dolor sit amet consectetur adipisicing, elit. Laboriosam ullam, quidem suscipit alias cum vitae cumque debitis repudiandae laudantium doloremque",
        //     content     : "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae, voluptas facilis! Eveniet blanditiis nulla sequi ut consectetur laudantium sit architecto, a quam repudiandae natus cupiditate, odio optio fugit, culpa sed modi accusamus cumque vero perspiciatis. Quam porro ut totam, odio vel architecto ex provident quo dolor fugit vitae, animi soluta voluptates illum labore magni aliquam quos tempora cum eligendi sit laborum odit atque. Qui fugiat nobis quae, neque nostrum reprehenderit accusamus voluptate, numquam aut unde aperiam obcaecati deleniti voluptatum debitis cum minima veritatis eius, incidunt sed soluta sint! Libero nihil quasi explicabo quos delectus, consectetur nemo soluta doloremque velit, mollitia.",
        //   },
        //   {
        //     title       : "Title 5",
        //     slug        : "title-5",
        //     description : "Lorem ipsum, dolor sit amet consectetur adipisicing, elit. Laboriosam ullam, quidem suscipit alias cum vitae cumque debitis repudiandae laudantium doloremque",
        //     content     : "Lorem, ipsum dolor sit amet consectetur adipisicing elit. Vitae, voluptas facilis! Eveniet blanditiis nulla sequi ut consectetur laudantium sit architecto, a quam repudiandae natus cupiditate, odio optio fugit, culpa sed modi accusamus cumque vero perspiciatis. Quam porro ut totam, odio vel architecto ex provident quo dolor fugit vitae, animi soluta voluptates illum labore magni aliquam quos tempora cum eligendi sit laborum odit atque. Qui fugiat nobis quae, neque nostrum reprehenderit accusamus voluptate, numquam aut unde aperiam obcaecati deleniti voluptatum debitis cum minima veritatis eius, incidunt sed soluta sint! Libero nihil quasi explicabo quos delectus, consectetur nemo soluta doloremque velit, mollitia.",
        //   },
        // ]
      }
    }
	}
</script>

<style scoped="">
  .aa{
    text-decoration: none;
  }
  .aa:hover{
    color: #2a6f97;
  }
</style>