<script setup>
import FirmSection from "../components/FirmSection.vue";
import ValuesSection from "../components/ValuesSection.vue";
import NotarySection from "../components/NotarySection.vue";
</script>

<template>
  <div class="about-page">
    <section class="about-intro">
      <div class="in">
        <RouterLink class="back-link" to="/">
          <span class="en">← Back to Home</span>
          <span class="km">← ត្រឡប់ទៅទំព័រដើម</span>
        </RouterLink>

        <p class="eyebrow">
          <span class="en">About Us</span>
          <span class="km">អំពីយើង</span>
        </p>

        <h1>
          <span class="en">
            Documents with certainty.
            <em>Service with integrity.</em>
          </span>

          <span class="km">
            ឯកសារដែលមានភាពច្បាស់លាស់
            <em>សេវាកម្មប្រកបដោយសុចរិតភាព</em>
          </span>
        </h1>

        <p class="lead">
          <span class="en">
            Learn about our firm, the values that guide our work, and the professional who
            supports your document needs.
          </span>

          <span class="km">
            ស្វែងយល់អំពីការិយាល័យ គោលការណ៍ការងារ
            និងអ្នកជំនាញដែលគាំទ្រតម្រូវការឯកសាររបស់លោកអ្នក។
          </span>
        </p>
      </div>
    </section>

    <FirmSection />
    <ValuesSection />
    <NotarySection />

    <section class="about-contact">
      <div class="in">
        <h2>
          <span class="en">How can we help you?</span>
          <span class="km">តើយើងអាចជួយលោកអ្នកយ៉ាងដូចម្តេច?</span>
        </h2>

        <p>
          <span class="en">
            Contact our office to discuss your documents and appointment requirements.
          </span>

          <span class="km">
            សូមទាក់ទងការិយាល័យ ដើម្បីពិភាក្សាអំពីឯកសារ និងតម្រូវការណាត់ជួបរបស់លោកអ្នក។
          </span>
        </p>

        <RouterLink class="btn" to="/contact">
          <span class="en">Contact Us →</span>
          <span class="km">ទាក់ទងយើង →</span>
        </RouterLink>
      </div>
    </section>
  </div>
</template>

<style scoped>
.about-intro {
  background: #f9f7f2;
  padding-block: 80px;
}

.in {
  max-width: 1520px;
  margin-inline: auto;
}

.back-link {
  display: inline-block;
  margin-bottom: 32px;
  color: #76603b;
  text-decoration: none;
}

h1 {
  max-width: 1050px;
  color: #16233a;
  font-size: clamp(2.4rem, 5vw, 4.8rem);
  line-height: 1.5;
}

h1 em {
  display: block;
  color: #b8893a;
  font-style: normal;
}

.lead {
  margin-top: 24px;
  font-size: 18px;
}

.about-contact {
  background: #071a2e;
  color: #fff;
  text-align: center;
}

.about-contact h2 {
  color: #fff;
}

.about-contact p {
  max-width: 650px;
  margin: 20px auto 28px;
  color: #c8d0dc;
}

@media (max-width: 600px) {
  .about-intro {
    padding-block: 48px;
  }

  .lead {
    font-size: 16px;
  }
}
</style>
