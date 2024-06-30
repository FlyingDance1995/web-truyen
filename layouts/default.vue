<script setup>
useSchemaOrg([
    {
        "@context": "http://schema.org",
        "@type": "Organization",
        "url": "https://monkeyd.vn",
        "foundingDate": "2024",
        "founders": [
            {
                "@type": "Person",
                "name": "MonkeyD"
            }],
        "contactPoint": {
            "@type": "ContactPoint",
            "contactType": "customer support",
            "telephone": "[0938 71 7000]",
            "email": "monkeyd.contact@gmail.com"
        },
        "sameAs": ["https://www.facebook.com/fanpage/"],
        "@id": "#organization",
        "name": "MonkeyD",
        "logo": "https://monkeyd.vn/images/logo/Logo-MonkeyD.png"
    }
])

import menu from "@/constants/menu.js";
import {userDarkMode} from "@/composables/state.js";

const route = useRoute();

const {isDarkMode, toggleDarkMode} = userDarkMode();

const tabValue = ref("/");
const isOpen = ref(false);
const aff = ref();

const handleAffLayerClick = () => {
    sessionStorage.setItem('aff', 'true');
    aff.value = true;
};

onMounted(() => {
    aff.value = sessionStorage.getItem('aff') !== null;
})

watch(() => route.path, () => {
    if (route?.path) {
        menu.forEach((item) => {
            if (route.path.includes(item.path)) {
                tabValue.value = item.path;
                isOpen.value = false;
            }
        });
    }
}, {immediate: true, deep: true});
</script>

<template>
    <!--ads-->
    <a v-if="!aff"
       id="affLayer"
       class="transparent-layer"
       href="https://s.shopee.vn/4KyL9eABIm"
       target="_blank"
       @click="handleAffLayerClick"></a>
    <!--wrapper-->
    <div class="wrapper">
        <!--start header wrapper-->
        <div class="header-wrapper">
            <!--start header -->
            <header>
                <div class="topbar d-flex align-items-center">
                    <nav class="navbar navbar-expand gap-3 container">
                        <div class="mobile-toggle-menu d-block d-lg-none" data-bs-toggle="offcanvas"
                             data-bs-target="#offcanvasNavbar">
                            <i class="bx bx-menu"></i>
                        </div>

                        <div class="topbar-logo-header d-flex">
                            <div class="">
                                <a href="https://monkeyd.vn">
                                    <img src="https://monkeyd.vn/images/logo/Logo-MonkeyD.png" class="logo-icon"
                                         alt="MonkeyD - Chuyên cập nhật các truyện tiểu thuyết, ngôn tình, truyện ngắn hot nhất 2024"
                                         width="120" height="30">
                                </a>
                            </div>
                        </div>

                        <div class="search-bar d-lg-block d-none">
                            <div class="position-relative popup-search w-100">
                                <form action="https://monkeyd.vn/tim-kiem" method="GET">
                                    <input class="form-control search-input form-control-lg ps-5" type="search"
                                           placeholder="Tìm truyện" name="search" value="" id="searchInputPC"
                                           style="max-height: 40px !important; min-height: inherit !important;">
                                    <span
                                        class="position-absolute top-50 search-show ms-3 translate-middle-y start-0 top-50 fs-4">
                                        <i class="bx bx-search"></i>
                                    </span>
                                </form>

                                <ul id="search-autocomplete">
                                    <li class="d-flex justify-content-start align-items-center mb-2 border-bottom">
                                        <a href="/trang-lan" class="m-2">
                                            <img src=""
                                                 alt="TRĂNG LẶN"
                                                 class="img-search">
                                        </a>

                                        <a href="/trang-lan" class="m-2 search-item-title">
                                            TRĂNG LẶN
                                        </a>
                                    </li>
                                </ul>
                            </div>
                        </div>

                        <div class="top-menu ms-auto">
                            <ul class="navbar-nav align-items-center gap-1">
                                <li class="nav-item mobile-search-icon d-flex d-lg-none" data-bs-toggle="modal"
                                    data-bs-target="#SearchModal">
                                    <a class="nav-link" href="javascript:;">
                                        <i class="bx bx-search"></i>
                                    </a>
                                </li>

                                <li class="nav-item dark-mode d-flex">
                                    <a class="nav-link dark-mode-icon" href="javascript:;" @click="toggleDarkMode">
                                        <i v-if="isDarkMode" class="bx bx-sun"></i>
                                        <i v-else class="bx bx-moon"></i>
                                    </a>
                                </li>
                            </ul>
                        </div>

                        <div class="d-flex justify-content-between">
                            <a href="https://monkeyd.vn/login" class="btn btn-sm btn-primary" style="margin-right: 5px">
                                Đăng nhập</a>
                            <a href="https://monkeyd.vn/tao-tai-khoan" class="btn btn-sm btn-primary">
                                Đăng ký
                            </a>
                        </div>
                    </nav>
                </div>
            </header>
            <!--end header -->
            <!--navigation-->
            <div class="primary-menu">
                <nav class="navbar navbar-expand-lg align-items-center">
                    <div class="container">
                        <div class="offcanvas offcanvas-start" tabindex="-1" id="offcanvasNavbar"
                             aria-labelledby="offcanvasNavbarLabel">
                            <div class="offcanvas-header border-bottom">
                                <div class="d-flex align-items-center">
                                    <div class="">
                                        <a href="https://monkeyd.vn">
                                            <img src="https://monkeyd.vn/images/logo/Logo-MonkeyD.png" class="logo-icon"
                                                 alt="MonkeyD - Chuyên cập nhật các truyện tiểu thuyết, ngôn tình, truyện ngắn hot nhất 2024">
                                        </a>
                                    </div>
                                </div>

                                <button type="button" class="btn-close" data-bs-dismiss="offcanvas"
                                        aria-label="Close">
                                </button>
                            </div>

                            <div class="offcanvas-body">
                                <ul class="navbar-nav align-items-center flex-grow-1">
                                    <li class="nav-item">
                                        <a class="nav-link" href="https://monkeyd.vn">
                                            <div class="menu-title d-flex align-items-center">Trang chủ</div>
                                        </a>
                                    </li>

                                    <li class="nav-item">
                                        <a class="nav-link" href="https://monkeyd.vn/truyen-moi.html">
                                            <div class="menu-title d-flex align-items-center">Truyện mới</div>
                                        </a>
                                    </li>

                                    <li class="nav-item dropdown">
                                        <a class="nav-link dropdown-toggle dropdown-toggle-nocaret" href="javascript:;"
                                           data-bs-toggle="dropdown">
                                            <div class="parent-icon"><i class="bx bx-list-ol"></i>
                                            </div>
                                            <div class="menu-title d-flex align-items-center">Thể loại</div>
                                            <div class="ms-auto dropy-icon"><i class="bx bx-chevron-down"></i></div>
                                        </a>

                                        <ul class="dropdown-menu scroll-menu ps ps--active-x ps--active-y ps--scrolling-y">
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/bach-hop.html">
                                                    <i class="bx bx-chevron-right"></i>Bách Hợp
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/be.html">
                                                    <i class="bx bx-chevron-right"></i>BE
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/chua-lanh.html">
                                                    <i class="bx bx-chevron-right"></i>Chữa Lành
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/co-dai.html">
                                                    <i class="bx bx-chevron-right"></i>Cổ Đại
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/cung-dau.html">
                                                    <i class="bx bx-chevron-right"></i>Cung Đấu
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/cuoi-truoc-yeu-sau.html">
                                                    <i class="bx bx-chevron-right"></i>Cưới Trước Yêu Sau
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/cuong-thu-hao-doat.html">
                                                    <i class="bx bx-chevron-right"></i>Cường Thủ Hào Đoạt
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/di-nang.html">
                                                    <i class="bx bx-chevron-right"></i>Dị Năng
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/dam-my.html">
                                                    <i class="bx bx-chevron-right"></i>Đam Mỹ
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/dien-van.html">
                                                    <i class="bx bx-chevron-right"></i>Điền Văn
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/do-thi.html">
                                                    <i class="bx bx-chevron-right"></i>Đô Thị
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/doan-van.html">
                                                    <i class="bx bx-chevron-right"></i>Đoản Văn
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/doc-tam.html">
                                                    <i class="bx bx-chevron-right"></i>Đọc Tâm
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/ga-thay.html">
                                                    <i class="bx bx-chevron-right"></i>Gả Thay
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/gia-dau.html">
                                                    <i class="bx bx-chevron-right"></i>Gia Đấu
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/gia-dinh.html">
                                                    <i class="bx bx-chevron-right"></i>Gia Đình
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hai-huoc.html">
                                                    <i class="bx bx-chevron-right"></i>Hài Hước
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hanh-dong.html">
                                                    <i class="bx bx-chevron-right"></i>Hành Động
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hao-mon-the-gia.html">
                                                    <i class="bx bx-chevron-right"></i>Hào Môn Thế Gia
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/he.html">
                                                    <i class="bx bx-chevron-right"></i>HE
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/he-thong.html">
                                                    <i class="bx bx-chevron-right"></i>Hệ Thống
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hien-dai.html">
                                                    <i class="bx bx-chevron-right"></i>Hiện Đại
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hoan-doi-than-xac.html">
                                                    <i class="bx bx-chevron-right"></i>Hoán Đổi Thân Xác
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/hoc-ba.html">
                                                    <i class="bx bx-chevron-right"></i>Học Bá
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hoc-duong.html">
                                                    <i class="bx bx-chevron-right"></i>Học Đường
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/hu-cau-ky-ao.html">
                                                    <i class="bx bx-chevron-right"></i>Hư Cấu Kỳ Ảo
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/huyen-huyen.html">
                                                    <i class="bx bx-chevron-right"></i>Huyền Huyễn
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/khong-cp.html">
                                                    <i class="bx bx-chevron-right"></i>Không CP
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/kinh-di.html">
                                                    <i class="bx bx-chevron-right"></i>Kinh Dị
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/linh-di.html">
                                                    <i class="bx bx-chevron-right"></i>Linh Dị
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/mat-the.html">
                                                    <i class="bx bx-chevron-right"></i>Mạt Thế
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/ngon-tinh.html">
                                                    <i class="bx bx-chevron-right"></i>Ngôn Tình
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/ngot.html">
                                                    <i class="bx bx-chevron-right"></i>Ngọt
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/nguoc.html">
                                                    <i class="bx bx-chevron-right"></i>Ngược
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/nguoc-luyen-tan-tam.html">
                                                    <i class="bx bx-chevron-right"></i>Ngược Luyến Tàn Tâm
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/nguoc-nam.html">
                                                    <i class="bx bx-chevron-right"></i>Ngược Nam
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/nguoc-nu.html">
                                                    <i class="bx bx-chevron-right"></i>Ngược Nữ
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/nhan-thu.html">
                                                    <i class="bx bx-chevron-right"></i>Nhân Thú
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/nu-cuong.html">
                                                    <i class="bx bx-chevron-right"></i>Nữ Cường
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/oe.html">
                                                    <i class="bx bx-chevron-right"></i>OE
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/phep-thuat.html">
                                                    <i class="bx bx-chevron-right"></i>Phép Thuật
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/phieu-luu.html">
                                                    <i class="bx bx-chevron-right"></i>Phiêu Lưu
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/phuong-dong.html">
                                                    <i class="bx bx-chevron-right"></i>Phương Đông
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/phuong-tay.html">
                                                    <i class="bx bx-chevron-right"></i>Phương Tây
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/quy-tac.html">
                                                    <i class="bx bx-chevron-right"></i>Quy tắc
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/se.html">
                                                    <i class="bx bx-chevron-right"></i>SE
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/showbiz.html">
                                                    <i class="bx bx-chevron-right"></i>Showbiz
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/sung.html">
                                                    <i class="bx bx-chevron-right"></i>Sủng
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/thanh-xuan-vuon-truong.html">
                                                    <i class="bx bx-chevron-right"></i>Thanh Xuân Vườn Trường
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/tien-hiep.html">
                                                    <i class="bx bx-chevron-right"></i>Tiên Hiệp
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/tieu-thuyet.html">
                                                    <i class="bx bx-chevron-right"></i>Tiểu Thuyết
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/tong-tai.html">
                                                    <i class="bx bx-chevron-right"></i>Tổng Tài
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/tra-thu.html">
                                                    <i class="bx bx-chevron-right"></i>Trả Thù
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/trong-sinh.html">
                                                    <i class="bx bx-chevron-right"></i>Trọng Sinh
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/va-mat.html">
                                                    <i class="bx bx-chevron-right"></i>Vả Mặt
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item" href="https://monkeyd.vn/the-loai/vo-tri.html">
                                                    <i class="bx bx-chevron-right"></i>Vô Tri
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/xuyen-khong.html">
                                                    <i class="bx bx-chevron-right"></i>Xuyên Không
                                                </a>
                                            </li>
                                            <li>
                                                <a class="dropdown-item"
                                                   href="https://monkeyd.vn/the-loai/xuyen-sach.html">
                                                    <i class="bx bx-chevron-right"></i>Xuyên Sách
                                                </a>
                                            </li>
                                            <div class="ps__rail-x" style="left: 0px; bottom: -485px; width: 224px;">
                                                <div class="ps__thumb-x" tabindex="0"
                                                     style="left: 0px; width: 201px;"></div>
                                            </div>
                                            <div class="ps__rail-y" style="top: 485px; right: 0px; height: 450px;">
                                                <div class="ps__thumb-y" tabindex="0"
                                                     style="top: 98px; height: 91px;"></div>
                                            </div>
                                        </ul>
                                    </li>

                                    <li class="nav-item">
                                        <a class="nav-link" href="https://monkeyd.vn/truyen-hoan-thanh.html">
                                            <div class="menu-title d-flex align-items-center">Truyện Full</div>
                                        </a>
                                    </li>

                                    <li class="nav-item">
                                        <a class="nav-link" href="https://monkeyd.vn/truyen-sang-tac.html">
                                            <div class="menu-title d-flex align-items-center">
                                                <div class="parent-icon">
                                                    <i class="bx bx-star"></i>
                                                </div>
                                                Truyện Sáng Tác
                                            </div>
                                        </a>
                                    </li>

                                    <li class="nav-item">
                                        <a class="nav-link" href="https://monkeyd.vn/danh-sach-nhom-dich">
                                            <div class="parent-icon">
                                                <i class="bx bx-group"></i>
                                            </div>
                                            <div class="menu-title d-flex align-items-center">Team</div>
                                        </a>
                                    </li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </nav>
            </div>
            <!--end navigation-->
        </div>
        <!--end header wrapper-->
        <!--start page wrapper -->
        <div class="page-wrapper">
            <div class="page-content">
                <slot/>
            </div>
        </div>
        <!-- search modal -->
        <div class="modal" id="SearchModal" tabindex="-1">
            <div class="modal-dialog modal-dialog-centered modal-dialog-scrollable modal-fullscreen-md-down">
                <div class="modal-content">
                    <div class="modal-header gap-2">
                        <div class="position-relative popup-search w-100">
                            <form action="https://monkeyd.vn/tim-kiem" method="GET">
                                <input
                                    class="form-control search-input form-control-lg ps-5 border border-3 border-primary"
                                    type="search" placeholder="Search" name="search" id="searchInputMobile">
                                <span
                                    class="position-absolute top-50 search-show ms-3 translate-middle-y start-0 top-50 fs-4"><i
                                    class="bx bx-search"></i></span>
                            </form>
                        </div>
                        <button type="button" class="btn-close d-md-none" data-bs-dismiss="modal"
                                aria-label="Close"></button>
                    </div>
                    <div class="modal-body">
                        <ul id="search-autocomplete-mobile" class="p-0"></ul>
                    </div>
                </div>
            </div>
        </div>
        <!-- end search modal -->
        <!-- Report Modal -->
        <div class="modal fade" id="reportLicenseModal" tabindex="-1" role="dialog"
             aria-labelledby="reportLicenseModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="reportLicenseModalLabel">Báo cáo tác phẩm vi phạm bản quyền</h5>
                    </div>
                    <div class="modal-body">
                        <form action="https://monkeyd.vn/report-license" method="POST" id="reportLicenseForm">
                            <input type="hidden" name="_token" value="4WaX9TUY3ErlMkX7fQc53tI3LQTKV6cA8FGI88GW">
                            <div class="mb-3">
                                <label for="violate_link" class="d-block"><b>Link tác phẩm vi phạm</b></label>
                                <input type="text" class="form-control" name="violate_link" id="violate_link"
                                       placeholder="Ex: https://monkeyd.vn/tac-pham-vi-pham.1/" required="">
                            </div>
                            <div class="mb-3">
                                <label for="original_link" class="d-block"><b>Link tác phẩm gốc</b></label>
                                <input type="text" class="form-control" name="original_link" id="original_link"
                                       placeholder="Ex: https://example.net/tac-pham-goc.1/" required="">
                            </div>
                            <div class="mb-3">
                                <label for="report_email" class="d-block"><b>Email liên hệ</b></label>
                                <input type="email" class="form-control" name="report_email" id="report_email"
                                       required="">
                            </div>
                            <div class="mb-3">
                                <label for="confirm_report">
                                    <input type="checkbox" name="confirm_report" id="confirm_report" required=""
                                           value="1"> Tôi cam kết báo cáo này là đúng sự thật
                                </label>
                            </div>
                            <div class="mb-3 d-flex justify-content-center">
                                <button type="submit" class="btn btn-danger btn-sm m-2">Gửi báo cáo</button>
                                <button type="button" class="btn btn-secondary btn-sm m-2 close" data-dismiss="modal"
                                        aria-label="Close" onclick="jQuery('#reportLicenseModal').modal('hide')">Huỷ
                                </button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
        <!--start overlay-->
        <div class="overlay toggle-icon"></div>
        <!--end overlay-->
        <!--Start Back To Top Button-->
        <a href="javaScript:;" class="back-to-top" style="display: inline;"><i class="bx bxs-up-arrow-alt"></i></a>
        <!--End Back To Top Button-->
        <footer class="page-footer">
            <div class="container py-2" style="text-align: left">
                <div class="row">
                    <div class="col-md-6">
                        <div class="footer-logo text-center">
                            <a href="https://monkeyd.vn">
                                <img src="https://monkeyd.vn/images/logo/Logo-MonkeyD.png"
                                     alt="MonkeyD - Chuyên cập nhật các truyện tiểu thuyết, ngôn tình, truyện ngắn hot nhất 2024"
                                     width="300" height="80">
                            </a>
                        </div>
                        <div class="footer-content my-3">
                            <p>Email: monkeyd.contact@gmail.com</p>
                            <p>Liên hệ hỗ trợ: https://www.fb.com/monkeyd.vn</p>
                            <button type="button" class="btn btn-sm btn-danger radius-30 px-3">
                                Báo cáo vi phạm bản quyền
                            </button>
                        </div>
                        <div class="footer-contact">

                        </div>
                    </div>
                    <div class="col-md-6">
                        <div class="footer-privacy">
                            <p>Mọi thông tin và hình ảnh trên website đều được bên thứ ba đăng tải, MonkeyD miễn trừ mọi
                                trách nhiệm liên quan đến các nội dung trên website này. Nếu làm ảnh hưởng đến cá nhân
                                hay tổ chức nào, khi được yêu cầu, chúng tôi sẽ xem xét và gỡ bỏ ngay lập tức. Các vấn
                                đề liên quan đến bản quyền hoặc thắc mắc khác, vui lòng liên hệ fanpage: <a
                                    href="https://www.facebook.com/profile.php?id=61557293151319" target="_blank">MonkeyD</a>
                            </p>
                        </div>
                    </div>
                </div>
            </div>
            <p class="mb-0 border-top pt-1">
                <a href="https://monkeyd.vn/page/chinh-sach-va-quy-dinh-chung.html"><b>Chính sách và quy định chung</b></a>
                - <a href="https://monkeyd.vn/page/chinh-sach-bao-mat.html"><b>Chính sách bảo mật</b></a> - <a
                href="https://monkeyd.vn/sitemap-index"><b>Sitemap</b></a><br>
                Copyright © 2024. All right reserved.
            </p>
        </footer>
    </div>
    <!--loading-->
    <div class="loading-modal">
        <div class="spinner-border text-primary" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
    </div>
</template>
