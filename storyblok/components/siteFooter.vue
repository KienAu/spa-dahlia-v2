<script setup>
    defineProps({
        blok: {
            type: Object,
            default: () => ({}),
        }
    })
</script>

<template>
    <section class="footer" id="contact">
        <footer class="container flexbox">
            <div class="flexbox flexbox__align-center flexbox__column--on-md">
                <div class="flexbox__column--is-w6 flexbox__column--is-md-w12">
                    <!-- 
                    <form class="footer__newsletter">
                        <label class="footer__newsletter__title">Join our newsletter</label>
                        <input class="footer__newsletter__input" type="email" placeholder="Email Address" />
                        <button type="submit"></button>
                        <small class="footer__newsletter__info">Sign up to receive special offers and exclusive news about Spa Dahlia.</small>
                    </form>
                    -->
                    <div class="footer__business-hours">
                        <h1 class="footer__business-hours__title">{{ blok.business_hours_title }}</h1>
                        <div class="flexbox footer__business-hours__day-times" v-for="item of blok.Business_hours" :key="item._uid" >
                            <span class="footer__business-hours__days">
                                {{ item.days }}
                            </span>
                            <span class="footer__business-hours__times">
                                {{ item.hours }}
                            </span>
                        </div>
                    </div>
                </div>
                <div class="flexbox__column--is-w6 flexbox__column--is-md-w12">
                    <div class="footer__contact">
                        <h1 class="footer__contact__title">{{ blok.address_title }}</h1>
                        <span class="footer__contact__address">{{ blok.address }}</span>
                        <span class="footer__contact__phone">{{ blok.phone }}<br>{{ blok.phone_2 }}</span>
                        <span class="footer__contact__email">{{ blok.email }}</span>
                        <ul class="footer__social">
                            <li class="footer__social__item" v-for="social of blok.social" :key="social._uid">
                                <a :href="social.link.url" class="footer__social__link">
                                    <img class="footer__social__image" :src="social.icon.filename" :alt="social.text" />
                                </a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </footer>
    </section>
</template>