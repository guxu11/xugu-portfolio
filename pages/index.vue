<template>
  <div>
    <section id="home" class="w3l-banner py-5">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6 col-sm-12 mt-lg-0 mt-4">
            <span class="title-small">Hello</span>
            <h1 class="mb-2 title"><span>I'm</span> {{ data.main.name }}</h1>
            <p>{{ data.main.occupation }}</p>
            <div class="mt-sm-5 mt-4">
              <nuxt-link to="/contact" class="btn btn-primary btn-style mr-2">
                Contact Me
              </nuxt-link>
              <nuxt-link
                to="/projects"
                class="btn btn-outline-primary btn-style mr-2"
              >
                Projects
              </nuxt-link>
            </div>
          </div>
          <div class="col-lg-6 col-md-8 col-sm-10 mt-lg-0 mt-4">
            <div class="img-effect text-lg-center">
              <img :src="data.main.image" alt="myphoto" class="small-img" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-index3" id="about">
      <div class="midd-w3 py-5">
        <div class="container py-lg-5 py-md-3">
          <div class="row">
            <div class="col-lg-4">
              <div class="position-relative">
                <img
                  :src="data.main.fullimage"
                  alt=""
                  class="radius-image img-fluid"
                />
              </div>
            </div>
            <div class="col-lg-8 mt-lg-0 mt-5">
              <h5 class="title-small mb-2">Who am i?</h5>
              <h3 class="title-big">
                I'm <b>{{ data.main.name }}</b
                >, a {{ data.main.occupation }}
              </h3>
              <p class="mt-4">{{ data.main.bio }}</p>
              <a
                :href="data.main.resumedownload"
                target="_blank"
                class="btn btn-style btn-primary mt-lg-5 mt-4"
                >Download Resume</a
              >
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-clients" id="clients">
      <div class="cusrtomer-layout py-5">
        <div class="container py-lg-5 py-md-4">
          <div class="heading text-center mx-auto">
            <h6 class="title-small text-center">Testimonials</h6>
            <h3 class="title-big mb-md-5 mb-4">
              What my collaborators think about Me
            </h3>
          </div>

          <div class="testimonial-width">
            <div class="row">
              <div
                class="col-md-6 col-sm-12 col-xs-12"
                v-for="testimonial in data.testimonials.testimonials"
                v-bind:key="testimonial"
              >
                <div class="item">
                  <div class="testimonial-content">
                    <div class="testimonial">
                      <blockquote>
                        <q>{{ testimonial.text }}</q>
                      </blockquote>
                      <div class="testi-des">
                        <div class="peopl align-self">
                          <h3>{{ testimonial.clientname }}</h3>
                          <p class="indentity">
                            {{ testimonial.clientaddress }}
                          </p>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="w3l-index5" id="about">
      <div class="new-block py-5">
        <div class="container py-lg-5">
          <div class="middle-section text-center">
            <h5 class="title-small mb-2">
              {{ data.main.quotes2.sectiontitle }}
            </h5>
            <div class="section-width">
              <h3 class="title-big">
                {{ data.main.quotes2.title }}
              </h3>
              <br>
              <h4>
                {{ data.main.quotes2.description }}
              </h4>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import data from "~/static/api/data.json";
export default {
  name: "index",
  data() {
    return {
      data: data,
    };
  },
  head() {
    return {
      title: "Home : " + this.data.main.name,
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

<style>
.small-img {
  max-width: 400px; /* Adjust the width as needed */
  max-height: 400px; /* Adjust the height as needed */
}
</style>
