<template>
  <div>
    <section class="w3l-about-breadcrumb text-center">
      <div class="breadcrumb-bg breadcrumb-bg-about py-sm-5 py-4">
        <div class="container py-2">
          <h2 class="title">My Projects</h2>
          <ul class="breadcrumbs-custom-path mt-2">
            <li><router-link to="/">Home</router-link></li>
            <li class="active">
              <span class="fa fa-arrow-right mx-2" aria-hidden="true"></span>
              Project
            </li>
          </ul>
        </div>
      </div>
    </section>

    <section class="w3l-services">
      <div class="blog py-5" id="services">
        <div class="container py-lg-5">
          <h5 class="title-small text-center">Projects list</h5>
          <h3 class="title-big text-center mb-sm-5 mb-4">
            I have done lots of projects.
          </h3>
          <div class="row">
            <div
              class="col-md-4 col-sm-12 col-xs-12"
              v-for="project in data.portfolio.projects"
              v-bind:key="project.no"
            >
              <div class="item">
                <div class="card">
                  <div class="box-wrap">
                    <a :href="project.url" target="_blank" class="card-link">
                      <div class="icon">
                        <span class="fa fa-pencil-square-o"></span>
                      </div>
                      <h4 class="number">{{ project.no }}</h4>
                      <h4>{{ project.title }}</h4>
                      <p class="description">{{ project.description }}</p>
                    </a>
                    <button
                      class="show-more"
                      @click.stop="showMore(project.description)"
                    >
                      Show more
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="mt-5 text-more">
            <p class="mt-4 pt-3 sample text-center"></p>
          </div>
        </div>
      </div>
    </section>

    <div class="abouthy-img-grids">
      <div class="img-one">
        <img src="/resources/assets/images/g5.jpg" alt=" " class="img-fluid" />
      </div>
      <div class="img-one content-mid">
        <center>
          <h3 class="title-big">Call me right now</h3>
          <br />
          <a href="" class="btn btn-style btn-primary">{{ data.main.phone }}</a>
        </center>
      </div>
      <div class="img-one">
        <img src="/resources/assets/images/g3.jpg" alt=" " class="img-fluid" />
      </div>
    </div>

    <!-- Modal -->
    <div v-if="showModal" class="modal">
      <div class="modal-content">
        <span class="close" @click="closeModal">&times;</span>
        <p>{{ modalContent }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import data from "~/static/api/data.json";
export default {
  name: "index",
  data() {
    return {
      data: data,
      showModal: false,
      modalContent: "",
    };
  },
  methods: {
    showMore(content) {
      this.modalContent = content;
      this.showModal = true;
    },
    closeModal() {
      this.showModal = false;
      this.modalContent = "";
    },
  },
  head() {
    return {
      title: "Project : " + this.data.main.name,
      meta: [
        {
          hid: "description",
          name: "description",
          content: "My custom description",
        },
      ],
    };
  },
};
</script>

<style scoped>
.card {
    position: relative;
    padding-bottom: 40px; /* Adjusted to make space for the button */
}

.card .description {
    overflow: hidden;
    display: -webkit-box;
    -webkit-line-clamp: 3; /* number of lines to show */
    -webkit-box-orient: vertical;
}

.show-more {
    position: absolute;
    bottom: 10px;
    right: 10px;
    background: none;
    border: none;
    color: #8e43e7; /* Set to the specified purple color */
    text-decoration: underline;
    cursor: pointer;
}

.show-more:hover {
    text-decoration: none;
}

.modal {
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgb(0,0,0);
    background-color: rgba(0,0,0,0.4);
}

.modal-content {
    background-color: #fefefe;
    margin: 15% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 80%;
    position: relative; /* Make sure the close button is positioned relative to the modal content */
}

.close {
    position: absolute; /* Position it absolutely to the modal content */
    top: 10px;
    right: 10px;
    color: #aaa;
    font-size: 28px;
    font-weight: bold;
}

.close:hover,
.close:focus {
    color: black;
    text-decoration: none;
    cursor: pointer;
}
</style>
