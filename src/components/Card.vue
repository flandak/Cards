<template>
  <ul class="container">
    <li
      class="card card--episode"
      v-for="index in 8"
      :key="index"
      :style="{ content: `'Item ' + (index + 1)` }"
    >
      <div class="card__index">{{ index }}</div>
      <p class="card__content">
        {{ parentMessage }}
      </p>
    </li>
  </ul>
</template>
<script>
export default {
  data() {
    return {
      parentMessage: `Lorem ipsum dolor sit amet consectetur adipisicing
        elit. Libero, dolorum rem rerum eum labore illum ut cum sequi animi
        ratione atque iure modi, quasi repellendus ducimus quo iusto nostrum
        officia.`,
    };
  },
};
</script>
<style scoped lang="scss">
.container {
  --gap: 2rem;
  display: grid;
  gap: var(--gap);
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 25ch), 1fr));
  .card {
    --skew: -5deg;
    display: flex;
    flex-direction: column;
    padding: 4.5rem 2rem;
    position: relative;
    min-height: 30rem;
    &:before {
      bottom: 0;
      content: "";
      left: 0;
      position: absolute;
      right: 0;
      top: 0;
      transform: skewY(var(--skew));
      z-index: -1;
    }
    &:after {
      bottom: 0;
      content: "";
      left: 0;
      position: absolute;
      right: 0;
      top: 0;
      transform: skewY(var(--skew));
      z-index: -1;
    }
    &__content {
      --gap: 1rem;
      display: grid;
      gap: var(--gap);
      justify-items: center;
      color: var(--color-text);
    }
    &__index {
      position: absolute;
      top: 0.5rem;
      right: 1rem;
      padding: 0.5rem 1rem;
      // background-color: var(--color-background-alt);
      color: var(--color-woodGreen);
      font-size: 26px;
      font-weight: bold;
      z-index: 1;
    }
  }
  .card--episode:before {
    background-image: linear-gradient(75deg, var(--gradient));
    border-radius: 0.25rem;
    height: calc(100% + 1px);
    top: -1px;
    transition: transform 0.24s ease-in;
  }

  .card--episode:hover:before {
    transform: skewY(var(--skew)) scale(1.03);
  }
  .card--episode:after {
    background-image: linear-gradient(
      to bottom,
      var(--color-background-alt-alpha),
      var(--color-background-alt) 0.75rem
    );
  }
}
@media (min-width: 80ch) {
  .card {
    --skew: -8deg;
  }
}
</style>
