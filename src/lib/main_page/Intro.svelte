<div class="intro" id="intro">
    <header>
        <nav>
            <ul>
                <li><a href="#about">About Me</a></li>
                <li><a href="#portfolio">Portfolio</a></li>
                <li><a href="#contact">My Contacts</a></li>
                <li><a href="/recipe">Random Cocktail</a></li>
            </ul>
        </nav>

        <div class="title">
            <h1>Vladimir Ryabenko</h1>
        </div>
    </header>
</div>

<style>
    .intro {
        height: 100vh;
        width: 100vw;
        position: fixed;
        color: white;
        background: url("/img/backgrounds/intro_back.jpg") fixed;
        background-size: cover;
    }

    ul {
        margin: 0;
        list-style: none;
        padding: 25px 0 5px;
        text-align: center;
        text-shadow: 0 0 7px white,
        0 0 42px aqua,
        0 0 82px aqua,
        0 0 92px aqua;
    }

    li {
        display: inline-block;
    }

    li:after {
        content: "|";
        color: aqua;
        display: inline-block;
        vertical-align: top;
    }

    li:last-child:after {
        content: none;
    }

    a {
        text-decoration: none;
        font-family: "Xirod", sans-serif;
        color: white;
        letter-spacing: 2px;
        position: relative;
        padding-bottom: 5px;
        margin: 0 34px 0 30px;
        font-size: 17px;
        text-transform: uppercase;
        display: inline-block;
        transition: color .2s;
    }

    a, a:visited {
        color: white;
    }

    a:hover {
        color: aqua;
    }

    a:before,
    a:after {
        content: "";
        position: absolute;
        height: 2px;
        top: auto;
        right: 50%;
        bottom: -5px;
        left: 50%;
        background: aqua;
        transition: .8s;
    }

    a:hover:before {
        left: 0;
    }

    a:hover:after {
        right: 0;
    }

    @media (max-width: 550px) {
        ul {
            padding-top: 0;
        }

        li {
            display: block;
        }

        li:after {
            content: none;
        }

        a {
            padding: 25px 0 20px;
            margin: 0 30px;
        }
    }

    .title {
        color: white;
        font-family: "Xirod", sans-serif;
        letter-spacing: 4px;
        font-size: 36px;
        display: flex;
        justify-content: center;
        text-align: center;
        margin-top: 20vh;
        text-shadow: 0 0 7px white,
        0 0 42px aqua;
    }
</style>