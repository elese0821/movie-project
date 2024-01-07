<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <router-link to="/">
                    <h1>
                        HELLO<span>MOVIE</span>
                    </h1>
                </router-link>
            </div>
        </div>
    </header>
</template>

<style lang="scss">
.header__inner {
    .header__nav {
        display: flex;
        justify-content: space-between;
        align-items: center;
        justify-content: center;

        a {
            display: flex;
            flex-direction: column;
            margin: 0.3rem 0;

            h1 {
                font-size: 1.5rem;
                color: var(--red);
                font-family: 'neurimboGothicRegular';
                display: inline-block;
                text-transform: capitalize;
                font-weight: 900;
                position: relative;
                text-align: center;
                line-height: 1.2;

                span {
                    font-size: 2rem;
                    color: var(--sub);
                    font-family: var(--mainfont-nexon);
                    font-weight: 400;
                    display: block;
                }
            }
        }
    }
}
</style>