<template>
    <div class="">
        <div class="d-none d-md-flex flex-column flex-shrink-0 p-3 text-bg-dark position-fixed top-0 bottom-0 text-start"
            style="width: 280px;">
            <a href="/" class="d-flex align-items-center mb-3 mb-md-0 me-md-auto text-white text-decoration-none">
                <svg class="bi pe-none me-2" width="40" height="32">
                    <use xlink:href="#bootstrap"></use>
                </svg>
                <span class="fs-4">Sidebar</span>
            </a>
            <hr>
            <ul class="nav nav-pills flex-column mb-auto">
                <li v-for="(link, index) in links" :key="index" class="nav-item my-1">
                    <button @click="selectMenu(index)"
                        :class="{ 'btn-primary': selectedMenu === index, 'text-white': selectedMenu !== index }"
                        class="btn rounded border-0 w-100">
                        <div class="btn-toggle collapsed" data-bs-toggle="collapse"
                            :data-bs-target="'#home-collapse' + index" aria-expanded="false">
                            <div class="d-flex align-items-center">
                                <i class="bi pe-2 fs-5 lh-1" :class="link.icon"></i>
                                <span>{{ link.name }}</span>
                            </div>
                        </div>
                    </button>
                    <div class="ms-3 ps-3 collapse" :id="'home-collapse' + index">
                        <ul class="btn-toggle-nav list-unstyled">
                            <li v-for="(sub, subIndex) in link.subMenu" :key="subIndex" class="mt-1">
                                <button @click="selectSubMenu(sub.id)"
                                    :class="{ 'btn-danger': selectedSubMenu === sub.id, 'text-white': selectedSubMenu !== sub.id }"
                                    class="btn rounded border-0 w-100">
                                    <div class="d-flex align-items-center">
                                        <i class="bi pe-2 fs-5 lh-1" :class="sub.icon"></i>
                                        <span>{{ sub.name }}</span>
                                    </div>
                                </button>
                            </li>
                        </ul>
                    </div>
                </li>

            </ul>
            <hr>
            <div class="dropdown">
                <a href="#" class="d-flex align-items-center text-white text-decoration-none dropdown-toggle"
                    data-bs-toggle="dropdown" aria-expanded="false">
                    <img src="https://github.com/mdo.png" alt="" width="32" height="32" class="rounded-circle me-2">
                    <strong>mdo</strong>
                </a>
                <ul class="dropdown-menu dropdown-menu-dark text-small shadow">
                    <li><a class="dropdown-item" href="#">New project...</a></li>
                    <li><a class="dropdown-item" href="#">Settings</a></li>
                    <li><a class="dropdown-item" href="#">Profile</a></li>
                    <li>
                        <hr class="dropdown-divider">
                    </li>
                    <li><a class="dropdown-item" href="#">Sign out</a></li>
                </ul>
            </div>
        </div>

        <div class="d-md-none d-sm-block">
            <div class="d-flex justify-content-end align-items-center px-3">
                <i class="bi bi-list btn btn-outline-dark" data-bs-toggle="offcanvas" data-bs-target="#offcanvasExample"
                    aria-controls="offcanvasExample"></i>
            </div>
            <div class="offcanvas offcanvas-start w-100" tabindex="-1" id="offcanvasExample"
                aria-labelledby="offcanvasExampleLabel">
                <div class="offcanvas-body p-0">
                    <div
                        class="w-100 d-flex flex-column flex-shrink-0 p-3 text-bg-dark position-fixed top-0 bottom-0 text-start">
                        <div class="d-flex align-items-center justify-content-between mb-3 text-white">
                            <span class="fs-4">Sidebar</span>
                            <i class="bi bi-x fs-4" data-bs-dismiss="offcanvas"></i>
                        </div>
                        <hr>
                        <ul class="nav nav-pills flex-column mb-auto">
                            <li v-for="(link, index) in links" :key="index" class="nav-item my-1">
                                <button @click="selectMenu(index)"
                                    :class="{ 'btn-primary': selectedMenu === index, 'text-white': selectedMenu !== index }"
                                    class="btn rounded border-0 w-100">
                                    <div class="btn-toggle collapsed" data-bs-toggle="collapse"
                                        :data-bs-target="'#home-collapse' + index" aria-expanded="false">
                                        <div class="d-flex align-items-center">
                                            <i class="bi pe-2 fs-5 lh-1" :class="link.icon"></i>
                                            <span>{{ link.name }}</span>
                                        </div>
                                    </div>
                                </button>
                                <div class="ms-3 ps-3 collapse" :id="'home-collapse' + index">
                                    <ul class="btn-toggle-nav list-unstyled">
                                        <li v-for="(sub, subIndex) in link.subMenu" :key="subIndex" class="mt-1">
                                            <button @click="selectSubMenu(sub.id)"
                                                :class="{ 'btn-danger': selectedSubMenu === sub.id, 'text-white': selectedSubMenu !== sub.id }"
                                                class="btn rounded border-0 w-100">
                                                <div class="d-flex align-items-center">
                                                    <i class="bi pe-2 fs-5 lh-1" :class="sub.icon"></i>
                                                    <span>{{ sub.name }}</span>
                                                </div>
                                            </button>
                                        </li>
                                    </ul>
                                </div>
                            </li>

                        </ul>
                        <hr>
                        <div class="dropdown">
                            <a href="#" class="d-flex align-items-center text-white text-decoration-none dropdown-toggle"
                                data-bs-toggle="dropdown" aria-expanded="false">
                                <img src="https://github.com/mdo.png" alt="" width="32" height="32"
                                    class="rounded-circle me-2">
                                <strong>mdo</strong>
                            </a>
                            <ul class="dropdown-menu dropdown-menu-dark text-small shadow">
                                <li><a class="dropdown-item" href="#">New project...</a></li>
                                <li><a class="dropdown-item" href="#">Settings</a></li>
                                <li><a class="dropdown-item" href="#">Profile</a></li>
                                <li>
                                    <hr class="dropdown-divider">
                                </li>
                                <li><a class="dropdown-item" href="#">Sign out</a></li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SideBar',
    data() {
        return {
            selectedMenu: null,
            selectedSubMenu: null,
            links: [
                {
                    id: 1,
                    name: 'Home',
                    icon: 'bi-house',
                    subMenu: [
                        {
                            id: 1,
                            name: 'overvew',
                            icon: 'bi-x'
                        },
                        {
                            id: 2,
                            name: 'test',
                            icon: 'bi-x'
                        },
                        {
                            id: 3,
                            name: 'overvew',
                            icon: 'bi-x'
                        },
                    ]
                },
                {
                    id: 2,
                    name: 'Orders',
                    icon: 'bi-grid'
                },
                {
                    id: 3,
                    name: 'Dashboard',
                    icon: 'bi-speedometer2',
                    subMenu: [
                        {
                            id: 23,
                            name: 'overvew',
                            icon: 'bi-x'
                        },
                        {
                            id: 34,
                            name: 'Weekly',
                            icon: 'bi-x'
                        },
                        {
                            id: 56,
                            name: 'Monthly',
                            icon: 'bi-x'
                        },
                    ]
                },
            ]
        }
    },
    methods: {
        selectMenu(index) {
            this.selectedMenu = index;
        },
        selectSubMenu(sId) {
            this.selectedSubMenu = sId;
        },

    }
}
</script>

<style lang="scss" scoped></style>