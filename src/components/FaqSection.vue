<script setup>
import { inject, onBeforeUnmount, onMounted, watch } from "vue";
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

const language = inject("language", null);
const animations = new Map();

function finish(details, expanded) {
  details.open = expanded;
  gsap.set(details, { clearProps: "height,overflow" });
  animations.delete(details);
}

function toggleAnswer(event) {
  event.preventDefault();
  const summary = event.currentTarget;
  const details = summary.parentElement;
  const previous = animations.get(details);
  const expanded = !(previous?.expanded ?? details.open);
  const startHeight = details.getBoundingClientRect().height;
  previous?.tween.kill();

  if (window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
    finish(details, expanded);
    ScrollTrigger.refresh();
    return;
  }

  // Measure the natural destination, then keep the answer rendered while closing.
  gsap.set(details, { clearProps: "height,overflow" });
  details.open = expanded;
  const endHeight = details.getBoundingClientRect().height;
  details.open = true;
  gsap.set(details, { height: startHeight, overflow: "hidden" });

  const tween = gsap.to(details, {
    height: endHeight,
    duration: 0.38,
    ease: "power2.inOut",
    onComplete: () => {
      finish(details, expanded);
      ScrollTrigger.refresh();
    },
  });
  animations.set(details, { tween, expanded });
}

function settleAnimations() {
  animations.forEach(({ tween, expanded }, details) => {
    tween.kill();
    finish(details, expanded);
  });
}

if (language) watch(language, settleAnimations);
onMounted(() => window.addEventListener("resize", settleAnimations));
onBeforeUnmount(() => {
  window.removeEventListener("resize", settleAnimations);
  settleAnimations();
});
</script>

<template>
  <section id="faq" class="alt faq">
    <div class="in faqgrid">
      <div class="list">
        <p class="eyebrow">FAQ</p>
        <h2>
          <span class="en">Common questions</span
          ><span class="km">សំណួរដែលសួរញឹកញាប់</span>
        </h2>
        <p class="intro">
          <span class="en"
            >Answers to common questions about our notarial services, documents and
            appointments.</span
          ><span class="km"
            >ចម្លើយចំពោះសំណួរទូទៅអំពីសេវាសារការី ឯកសារ និងការណាត់ជួប។</span
          >
        </p>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">Which documents should I bring?</span
            ><span class="km">តើត្រូវនាំឯកសារអ្វីខ្លះ?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">Do I need to attend in person?</span
            ><span class="km">តើត្រូវមកដោយផ្ទាល់ទេ?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">Do I need an appointment?</span
            ><span class="km">តើត្រូវណាត់ជួបជាមុនទេ?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">How are fees determined?</span
            ><span class="km">តើថ្លៃសេវាកំណត់យ៉ាងដូចម្តេច?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">How long does the service take?</span
            ><span class="km">តើសេវាចំណាយពេលប៉ុន្មាន?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">Can documents be prepared for use abroad?</span
            ><span class="km">តើអាចរៀបចំឯកសារសម្រាប់ប្រើក្រៅប្រទេសបានទេ?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
        <details>
          <summary @click="toggleAnswer">
            <span class="en">Which languages does the office support?</span
            ><span class="km">ការិយាល័យគាំទ្រភាសាអ្វីខ្លះ?</span>
          </summary>
          <p>
            <span class="pending"
              ><span class="en">Pending</span><span class="km">រង់ចាំ</span></span
            ><span class="en">Answer to be supplied by the client.</span
            ><span class="km">ចម្លើយត្រូវផ្តល់ដោយអតិថិជន។</span>
          </p>
        </details>
      </div>
      <img class="scales" src="/images/website-4.jpeg" alt="Golden scales of justice" />
    </div>
  </section>
</template>
