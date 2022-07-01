<script>
    import { base } from '$app/paths';
</script>

<div class="contact" id="contact">
    <h1>Contact Me</h1>

    <div class="contact-links">
        <a href="https://github.com/Vldmr314" target="_blank"><img src="{base}/img/socials/git_icon.png"
                                                                   alt="github"/></a>
        <a href="https://vk.com/vladimir31415" target="_blank"><img src="{base}/img/socials/vk_icon.png" alt="vk"/></a>
        <a href="https://www.instagram.com/_.mr_volodya._" target="_blank"><img src="{base}/img/socials/inst_icon.png"
                                                                                alt="instagram"/></a>
        <a href="https://t.me/Vldmr11" target="_blank"><img src="{base}/img/socials/tg_icon.png" alt="telegram"/></a>
    </div>

    <footer>
        <p>© Rights reserved 2022</p>
    </footer>
</div>

<style>
    .contact {
        margin: 0;
        position: absolute;
        top: 300vh;
        height: 100vh;
        width: 100vw;
        background: url("https://github.com/Vldmr314/PersonalWebsite/tree/master/static/img/backgrounds/contact_back.jpeg") no-repeat;
        background-size: cover;
        color: white;
    }

    h1 {
        font-family: "Xirod", sans-serif;
        letter-spacing: 3px;
        font-size: 46px;
        display: flex;
        justify-content: center;
        margin-top: 5vh;
    }

    .contact-links {
        display: flex;
        flex-wrap: wrap;
        flex-direction: column;
        align-items: center;
        margin: 0 auto;
        max-width: 640px;
        padding: 16px 8px 0 8px;
    }

    a {
        margin-top: 9%;
    }

    img {
        transition: 0.2s;
        width: 48px;
        will-change: filter;
    }

    img:hover {
        transform: scale(1.2);
    }

    footer {
        display: flex;
        text-align: center;
    }

    p {
        position: absolute;
        left: 0;
        right: 0;
        bottom: 1vh;
        z-index: 10;
    }
</style>