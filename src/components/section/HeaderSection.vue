<template>
    <header id="header" role="banner">
        <div class="header__inner">
            <div class="header__nav">
                <h1>let's <span>movie</span></h1>
                <nav>
                    <ul>
                        <li><a href="#">월간 Top10</a></li>
                        <li><a href="#">주간 Top10</a></li>
                    </ul>
                </nav>
            </div>

            <div class="info_box"
                style="backgroundImage: url(https://image.tmdb.org/t/p/w500/kjQBrc00fB2RjHZB3PGR4w9ibpz.jpg)">
                <div class="container">
                    <div class="left play__icon">
                        <a href="#" class="info_poster">
                            <img src='https://image.tmdb.org/t/p/w500//vFsSluuzqxR46Ils9ib52ItdE9u.jpg' alt="dd">
                        </a>
                    </div>
                    <div class="right">
                        <div class="detail_tit">
                            <h2>크리에이터</h2>
                            <p>The Creator, 2023</p>
                        </div>

                        <div class="detail_cont">
                            <div class="inner_cont">
                                <dl class="list_cont">
                                    <dt>개봉</dt>
                                    <dd class="dd_type">
                                        2023-09-27
                                    </dd>
                                </dl>


                                <dl class="list_cont">
                                    <dt>장르</dt>
                                    <dd class="dd_type">
                                        <span>
                                            액션/모험/드라마
                                        </span>
                                    </dd>
                                </dl>

                                <dl class="list_cont">
                                    <dt>국가</dt>
                                    <dd>Canada</dd>
                                </dl>

                                <dl class="list_cont">
                                    <dt>러닝타임</dt>
                                    <dd>134분</dd>
                                </dl>

                            </div>

                            <div class="inner_cont right_cont">
                                <dl class="list_cont">
                                    <dt>평점 </dt>
                                    <dd>
                                        <span class='ico_movie ico_star'>
                                        </span>
                                        7.1
                                    </dd>
                                </dl>


                            </div>

                        </div>


                        <dl class="list_cont last_cont">
                            <dt>주요정보</dt>
                            <dd class="line8">인류를 지키기 위해 만들어진 AI가 LA에 핵폭탄을 터뜨린 후, 인류와 AI 간의 피할 수 없는 전쟁이 시작된다. 전직 특수부대 요원
                                ‘조슈아’는 실종된 아내의 단서를 얻을지도 모른다는 생각에 전쟁을 끝내기 위한 인류의 작전에 합류한다. 인류를 위협할 강력한 무기와 이를 창조한 ‘창조자’를 찾아
                                나서고, 그 무기가 아이 모습의 AI 로봇 '알피'란 사실을 알게 되는데… 인간적인가, 인간의 적인가? 10월, SF 블록버스터의 신세계가 펼쳐진다!</dd>
                        </dl>
                    </div>
                </div>
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

        h1 {
            font-size: 1.8rem;
            color: var(--red);
            font-family: var(--mainfont-nexon);
            padding: 5px 1rem;
            margin: 20px 10px;
            display: inline-block;
            text-transform: capitalize;
            font-weight: 900;
            position: relative;

            span {
                font-size: 1.8rem;
                color: var(--sub);
                font-family: var(--mainfont-nexon);
                font-weight: 400;
                margin-left: -0.3rem;
            }
        }

        nav {
            li {
                display: inline;

                a {
                    display: inline-block;
                    padding: 10px;
                }
            }
        }
    }

}

.info_box {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    position: relative;
    padding: 30px;

    &::before {
        content: '';
        width: 100%;
        height: 100%;
        position: absolute;
        left: 0;
        top: 0;
        background-color: #00000032;
        backdrop-filter: blur(7px);
        z-index: 1;
    }

    .container {
        display: flex;
        justify-content: flex-start;
        position: relative;
        z-index: 10;

        .left {
            width: 350px;

        }

        .right {
            width: calc(100% - 390px);
            background-color: rgba(0, 0, 0, .6);
            padding: 2rem;
            letter-spacing: 0.05rem;

            .detail_tit {

                h2 {
                    font-size: 1.8rem;
                    font-weight: 700;
                }
            }

            .detail_cont {
                display: flex;
                align-items: flex-start;
                margin-top: 2rem;

                .right_cont {
                    margin-left: 2rem;
                }

                .inner_cont {
                    display: table;
                    max-width: 60%;

                    .list_cont {
                        line-height: 1.7;
                        display: table-row;

                    }

                }

            }

            .last_cont {
                margin-top: 1rem;

                dt {
                    display: flex;
                    background-color: #c93131;
                    border-radius: 10px;
                    justify-content: center;
                    align-items: center;
                    margin-bottom: 0.5rem;
                    color: #fff;
                    padding-right: 0;
                }

                .line8 {
                    line-height: 1.8;
                    overflow: auto;
                    text-overflow: ellipsis;
                    display: -webkit-box;
                    -webkit-line-clamp: 6;
                    -webkit-box-orient: vertical;

                    &::-webkit-scrollbar {
                        width: 10px;
                    }

                    &::-webkit-scrollbar-thumb {
                        background-color: #888888;
                        border-radius: 2px;
                    }

                    &::-webkit-scrollbar-track {
                        background-color: rgb(15, 15, 15);
                        border-radius: 2px;
                    }

                }

            }
        }
    }
}



dt {
    max-width: 100px;
    font-weight: normal;
    white-space: nowrap;
    display: table-cell;
    color: rgb(122, 122, 122);
    padding-right: 1rem;

}

dd {
    display: table-cell;

    .star {
        width: 20px;
        height: 20px;
    }


    .font_color {
        color: rgb(128, 128, 128)
    }

}


.ico_movie,
.ico_logo {
    display: inline-block;
    overflow: hidden;
    font-size: 0;
    line-height: 0;
    text-indent: -9999px;
    vertical-align: top;
    background: url('../../assets/img/ico_movie.png') no-repeat 0 0;
}

.ico_star {
    width: 13px;
    height: 13px;
    margin: 6px 2px 0 0;
    background-position: -200px -40px;
}
</style>