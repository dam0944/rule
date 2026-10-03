<script setup>
import ContactSection from "../components/ContactSection.vue";
import MapSection from "../components/MapSection.vue";
import PrepareSection from "../components/PrepareSection.vue";
</script>

<template>
  <div class="contact-page">
    <section class="contact-page-intro">
      <div class="in">
        <RouterLink class="back-link" to="/">
          <span class="en">← Back to Home</span>
          <span class="km">← ត្រឡប់ទៅទំព័រដើម</span>
        </RouterLink>

        <p class="eyebrow">
          <span class="en">Contact Our Office</span>
          <span class="km">ទាក់ទងការិយាល័យរបស់យើង</span>
        </p>

        <h1>
          <span class="en">Let’s discuss your documents.</span>
          <span class="km">ពិភាក្សាអំពីឯកសាររបស់លោកអ្នក។</span>
        </h1>

        <p class="lead">
          <span class="en">
            Tell us what you need. Our office will confirm the requirements and arrange
            your appointment.
          </span>
          <span class="km">
            សូមប្រាប់យើងពីតម្រូវការរបស់លោកអ្នក។ ការិយាល័យនឹងបញ្ជាក់ឯកសារត្រូវការ
            និងរៀបចំការណាត់ជួប។
          </span>
        </p>
      </div>
    </section>

    <ContactSection />
    <MapSection />
    <PrepareSection />
  </div>
</template>

<style scoped>
.contact-page-intro {
  background: #f9f7f2;
  padding-block: 70px;
}

.back-link {
  display: inline-block;
  margin-bottom: 32px;
  color: #76603b;
  text-decoration: none;
}

h1 {
  max-width: 1000px;
  color: #16233a;
  font-size: clamp(2.4rem, 5vw, 4.6rem);
  line-height: 1.5;
}

.lead {
  margin-top: 24px;
  font-size: 18px;
}

@media (max-width: 600px) {
  .contact-page-intro {
    padding-block: 48px;
  }

  .lead {
    font-size: 16px;
  }
}
</style>
