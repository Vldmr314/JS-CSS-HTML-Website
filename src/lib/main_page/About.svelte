<script>
    import { base } from '$app/paths';
</script>

<div class="about" id="about">
    <h1>About me</h1>

    <div class="about-wrapper">
        <div class="about-info">
            <p>Hi! My name is Vladimir Ryabenko and you are currently on my personal website:) This is only the
                first version, so please don't judge strictly. I am a first year student at Innopolis University
                and a beginner developer!</p>
            <img src="{base}/img/other/my_photo.jpg" alt="Vladimir Ryabenko" height="450"/>
        </div>
    </div>
</div>

<style>
    .about {
        margin: 0;
        position: absolute;
        top: 100vh;
        height: 100vh;
        width: 100vw;
        background: url("%sveltekit.assets%/img/backgrounds/about_back.jpg") fixed;
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

    .about-wrapper {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
    }

    .about-info {
        display: flex;
        justify-content: space-between;
        margin-bottom: 20px;
        width: 55%;
    }

    img {
        box-shadow: 0 0 7px white,
        0 0 42px aqua;
    }

    p {
        width: 50%;
        color: white;
        font-family: "Xirod", sans-serif;
        letter-spacing: 2px;
        font-size: 22px;
    }
</style>