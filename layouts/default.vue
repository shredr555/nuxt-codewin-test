<template lang='pug'>
div.page
    header.header
        .container
            .header__top
                .header__info
                    IconPoin.header__icon(:fontControlled='false')
                    a г. Красноярск, ул. Телевизорная 1, стр. 14, оф. 204
                .header__info
                    IconPhone.header__icon(:fontControlled='false')
                    a +7 (391) 209 57-57
                .header__info
                    IconPhone.header__icon(:fontControlled='false')
                    a +7 (391) 215 54-33
                .header__info
                    IconLetter.header__icon(:fontControlled='false')
                    a los-bio@mail.ru
                .header__info
                    IconArrowBack.header__icon(:fontControlled='false')
                    a Заказать звонок
            .header__nav
                IconLogo.header__logo(:fontControlled='false')
                nav.nav
                    NuxtLink(to='/') О компании
                    NuxtLink(to='/') Проекты
                    NuxtLink(to='/') Каталог
                    NuxtLink(to='/') Контакты
                a.header__btn Получить КП
    main.layout__main
        NuxtPage
    footer.footer
        .container.footer__container
            .footer__logo
                IconLogo.footer__logo-icon(:fontControlled='false')
                h5 ООО «ТОРГОВЫЙ ДОМ «ЛОС-БИО»
                ul.footer__details
                    li #[span ИНН:] 2463123719 #[span КПП:] 246301001
                    li #[span ОГРН:] 1212400008688
            .footer__nav
                h5 Компания
                ul
                    li 
                        NuxtLink(to='/') О компании
                    li 
                        NuxtLink(to='/') Проекты
                    li 
                        NuxtLink(to='/') Каталог
                    li 
                        NuxtLink(to='/') Контакты
            .footer__nav
                h5 Каталог
                ul
                    li 
                        NuxtLink(to='/') КНС
                    li 
                        NuxtLink(to='/') Емкости
                    li 
                        NuxtLink(to='/') 
                            | Ливневые 
                            br 
                            | очистные-сооружения
                    li 
                        NuxtLink(to='/') 
                            | Хозяйственно-бытовые 
                            br
                            | очистные сооружения
                    li 
                        NuxtLink(to='/') Комплектующие
            .footer__nav
                h5 Контакты
                ul
                    li
                        IconPhone.footer__nav-icon 
                        a +7 (391) 209-57-57
                    li
                        IconPhone.footer__nav-icon 
                        a +7 (391) 209-57-57
                    li
                        IconLetter.footer__nav-icon   
                        a los-bio@mail.ru
                    li
                        IconArrowBack.footer__nav-icon  
                        a Заказать звонок
                    li 
                        a.footer__btn Получить КП
</template>

<script setup lang="ts">
    import IconLogo from '~/assets/logo.svg'
    import IconPoin from '~/assets/Vector.svg'
    import IconPhone from '~/assets/Vector-1.svg'
    import IconLetter from '~/assets/Vector-2.svg'
    import IconArrowBack from '~/assets/Vector-3.svg'
</script>