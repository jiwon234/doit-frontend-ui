<template>
    <section class="maincontents">
        <section class="mainbanner"><img src="/images/mainimg.png" /></section>
        <section class="newbook">
            <h1 class="maintit">
                새로 나온 도서<span>분야별로 새로 나온 도서를 만나 보세요</span>
            </h1>
            <div class="tapcontent">
                <div class="tap">
                    <b-button variant="tap active" @click="AddContents('Newbooks_it')">IT 전문서</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_work')">업무 능력, 기타</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_photo')">사진 예술</b-button>
                    <b-button variant="tap" @click="AddContents('Newbooks_science')">데이터 과학</b-button>
                </div>
                <VueSlickCarousel class="mainslider" v-bind="settings">
                    <div class="rollimg" v-for="(item, index) in Newbooks" :key="index">
                        <span class="imgbox"><img :src="item.imgurl" /></span>
                        <strong v-html="item.name"></strong>
                        <span class="textbox" v-html="item.subdec"></span>
                    </div>
                </VueSlickCarousel>                
            </div>
        </section>
        <section class="searchbook">
            <h1 class="maintit">
                도서 검색<span>찾고자 하는 도서명을 검색해 주세요</span>
            </h1>
        </section>
        <section class="bannermenu">
            <div class="itembox"
                v-for="(item, index) in mainbanner" 
                :key="index"
                @click="gotoPage(item.url)"
                >
                <span v-html="item.stitle"></span>
                <strong v-html="item.maintit"></strong>
                <i class="bi" :class="item.iconame"></i>
            </div> 
        </section>
        <section class="notice">
            <div class="noticebox">
                <h1 class="maintit">공지 사항</h1>
                <b-button variant="noticemore" @click="viewmore($event)"/>
                <div class="newsitem" v-for="(item, index) in noticelists" :key="index">
                    <strong v-html="item.noticetit"></strong>
                    <span v-html="item.date"></span>
                </div>
            </div>
        </section>
    </section>
</template>

<script>
import { _ } from 'core-js';

export default {
    data() {
        return {
            Newbooks: [],
            Newbooks_it: [
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
                {
                    imgurl: "/images/books_image/book01.jpg",
                    name: "Do it! 웹사이트 따라 만들기",
                    subdec: "HTML, CSS, 자바스크립트 문법서는 공부했지만, 웹사이트를...",
                },
            ],
            Newbooks_work: [
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
                {
                    imgurl: "/images/books_image/book08.jpg",
                    name: "된다! 엑셀 수식 & 함수",
                    subdec: "매일 쓰는 엑셀이 매번 어렵게 느껴지는 건 너무 많은 기능을...",
                },
            ],
            Newbooks_photo: [
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
                {
                    imgurl: "/images/books_image/book15.jpg",
                    name: "포토샵 보정&합성 디자인 사전",
                    subdec: "포토샵 사진 보정, 합성 때문에 고민인가요? 한 권으로 상위...",
                },
            ],
            Newbooks_science: [
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
                {
                    imgurl: "/images/books_image/book21.jpg",
                    name: "블록체인 무엇인가?",
                    subdec: "이 책은 과장된 소문에 휘둘리지도, 비트코인에 집중하지도 않는..."
                },
            ],
            settings: {
                slidesToShow: 5, // 화면에 나타날 슬라이드 개수
                arrows: true, // 버튼 사용 여부
                dots: false, // 하단 버튼 사용 여부
                infinite: true, // 슬라이트 반복 여부
                responsive: [
                    {
                        breakpoint: 767, // 브라우저 크기가 767 이하일 때
                        settings: {
                            slidesToShow: 4,
                        },
                    },
                    {
                        breakpoint: 414, // 브라우저 크기가 464 이하일 때
                        settings: {
                            slidesToShow: 2,
                        },
                    },
                ],
            },
            /*배너 만들기*/
            mainbanner: [
                {
                    stitle: "교수 및 강사 전용",
                    maintit: "교재 샘플/강의 자료",
                    iconname: "bi-stickies",
                    url: "/classsample",
                },
                {
                    stitle: "스터디 카페",
                    maintit: "Do it! 스터디룸",
                    iconname: "bi-book-half",
                    url: "https://cafe.naver.com/doitstudyroom",
                },
                {
                    stitle: "이지스 SNS",
                    maintit: "페이스북",
                    iconname: "bi-facebook",
                    url: "https://www.facebook.com/easyspub/",
                },
            ],
            noticelists: [
                {
                    noticetit: "이지스퍼블리싱/이지스에듀 저작물 이용 지침",
                    date: "2023.03.30",
                },
                {
                    noticetit: "IT 분야 편집/기획자 모집",
                    date: "2023.02.16",
                },
                {
                    noticetit:"이지스퍼블리싱 전자책 대여 서비스 오픈!",
                    date: "2021.10.28",
                },
            ],
        };
    },
    created() {
        this.Newbooks = this.Newbooks_it;
    },
    methods: {
        AddContents(contents) {
            this.Newbooks = this[contents];
            document.querySelector(".active").classList.remove("active"); // 현재 active인 것 지우고, target에 active 클래스 추가 
            event.target.classList.add("active");
        },
        gotoPage(url) {
            if (url == "/classsample") {
                this.$router.push(url);
            } else {
                window.open(url, "_blank");
            }
        },
        viewmore(event) {
            if (event.target.parentElement.classList.value.indexOf("full") > -1) {
                event.target.parentElement.classList.remove("full");
            }
            else {
                event.target.parentElement.classList.add("full");
            }
        },
    },
};
</script>