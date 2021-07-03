<template>
  <main class="content">
    <form action="#" method="post">
      <div class="content__wrapper">
        <h1 class="title title--big">Конструктор пиццы</h1>
        <div class="content__dough">
          <div class="sheet">
            <h2 class="title title--small sheet__title">Выберите тесто</h2>
            <div class="sheet__content dough">
              <label
                v-for="(element, index) in pizza.dough"
                :key="index"
                :class="`dough__input dough__input--${
                  DOUGH_ENGLISH[element.name]
                }`"
              >
                <input
                  type="radio"
                  name="dough"
                  :value="DOUGH_ENGLISH[element.name]"
                  class="visually-hidden"
                  :checked="index === 0 ? true : false"
                />
                <b>{{ element.name }}</b>
                <span>{{ element.description }}</span>
              </label>
            </div>
          </div>
        </div>
        <div class="content__diameter">
          <div class="sheet">
            <h2 class="title title--small sheet__title">Выберите размер</h2>
            <div class="sheet__content diameter">
              <label
                v-for="(element, index) in pizza.sizes"
                :key="index"
                :class="`diameter__input diameter__input--${
                  PIZZA_MULTIPLIER_TO_SIZE[element.multiplier]
                }`"
              >
                <input
                  type="radio"
                  name="diameter"
                  :value="PIZZA_MULTIPLIER_TO_SIZE[element.multiplier]"
                  class="visually-hidden"
                  :checked="index === pizza.sizes.length - 1 ? true : false"
                />
                <span>{{ element.name }}</span>
              </label>
            </div>
          </div>
        </div>
        <div class="content__ingridients">
          <div class="sheet">
            <h2 class="title title--small sheet__title">
              Выберите ингридиенты
            </h2>
            <div class="sheet__content ingridients">
              <div class="ingridients__sauce">
                <p>Основной соус:</p>
                <label
                  v-for="(element, index) in pizza.sauces"
                  :key="index"
                  class="radio ingridients__input"
                >
                  <input
                    type="radio"
                    name="sauce"
                    :value="SAUCE_NAME_TO_VALUE[element.name]"
                    :checked="index === 0 ? true : false"
                  />
                  <span>{{ element.name }}</span>
                </label>
              </div>
              <div class="ingridients__filling">
                <p>Начинка:</p>
                <ul class="ingridients__list">
                  <li
                    v-for="(element, index) in pizza.ingredients"
                    :key="index"
                    class="ingridients__item"
                  >
                    <span
                      :class="`filling filling--${
                        INGREDIENTS_ENGLISH[element.name]
                      }`"
                    >
                      {{ element.name }}
                    </span>
                    <div class="counter counter--orange ingridients__counter">
                      <button
                        type="button"
                        class="
                          counter__button
                          counter__button--disabled
                          counter__button--minus
                        "
                      >
                        <span class="visually-hidden">Меньше</span>
                      </button>
                      <input
                        type="text"
                        name="counter"
                        class="counter__input"
                        value="0"
                      />
                      <button
                        type="button"
                        class="counter__button counter__button--plus"
                      >
                        <span class="visually-hidden">Больше</span>
                      </button>
                    </div>
                  </li>
                </ul>
              </div>
            </div>
          </div>
        </div>
        <div class="content__pizza">
          <label class="input">
            <span class="visually-hidden">Название пиццы</span>
            <input
              type="text"
              name="pizza_name"
              placeholder="Введите название пиццы"
            />
          </label>
          <div class="content__constructor">
            <div class="pizza pizza--foundation--big-tomato">
              <div class="pizza__wrapper">
                <div class="pizza__filling pizza__filling--ananas"></div>
                <div class="pizza__filling pizza__filling--bacon"></div>
                <div class="pizza__filling pizza__filling--cheddar"></div>
              </div>
            </div>
          </div>
          <div class="content__result">
            <p>Итого: 0 ₽</p>
            <button type="button" class="button button--disabled" disabled>
              Готовьте!
            </button>
          </div>
        </div>
      </div>
    </form>
  </main>
</template>

<script>
import misc from "@/static/misc.json";
import pizza from "@/static/pizza.json";
import user from "@/static/user.json";
import {
  PIZZA_MULTIPLIER_TO_SIZE,
  SAUCE_NAME_TO_VALUE,
  INGREDIENTS_ENGLISH,
  DOUGH_ENGLISH,
} from "@/common/const.js";

export default {
  name: "Index",
  data() {
    return {
      misc,
      pizza,
      user,
      PIZZA_MULTIPLIER_TO_SIZE,
      SAUCE_NAME_TO_VALUE,
      INGREDIENTS_ENGLISH,
      DOUGH_ENGLISH,
    };
  },
};
</script>

<style lang="scss" scoped></style>
