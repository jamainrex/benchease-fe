<template>
  <aside class="col-auto col-md-3 col-xl-2 px-sm-2 px-0 theme-bg-color">
    <div
      class="d-flex flex-column align-items-center align-items-sm-start w-100 px-3 pt-2 text-white min-vh-100"
    >
      <a
        href="/"
        class="d-flex align-items-center pb-3 mx-auto text-decoration-none"
      >
        <span class="fs-5 d-none d-sm-inline text-white">
          <img alt="Vue logo" src="../assets/logo.png" />
        </span>
      </a>
      <ul
        class="nav nav-pills flex-column mb-sm-auto mb-0 align-items-center align-items-sm-start w-100"
        id="menu"
      >
        <li class="nav-item">
          <a href="#" class="nav-link align-middle px-0">
            <i class="fs-4 bi-house"></i>
            <span class="ms-1 d-none d-sm-inline text-white">Dashboard</span>
          </a>
        </li>
        <li>
          <a
            href="#submenu1"
            data-bs-toggle="collapse"
            class="nav-link px-0 align-middle"
          >
            <i class="fs-4 bi-speedometer2"></i>
            <span class="ms-1 d-none d-sm-inline text-white">Skills</span>
          </a>
          <!-- <ul
            class="collapse show nav flex-column ms-1"
            id="submenu1"
            data-bs-parent="#menu"
          >
            <li class="w-100">
              <a href="#" class="nav-link px-0">
                <span class="d-none d-sm-inline">Item</span> 1
              </a>
            </li>
            <li>
              <a href="#" class="nav-link px-0">
                <span class="d-none d-sm-inline">Item</span> 2
              </a>
            </li>
          </ul> -->
        </li>
        <li>
          <a href="#" class="nav-link px-0 align-middle">
            <i class="fs-4 bi-table"></i>
            <span class="ms-1 d-none d-sm-inline text-white">Settings</span></a
          >
        </li>
        <li>
          <a
            href="#submenu2"
            data-bs-toggle="collapse"
            class="nav-link px-0 align-middle"
          >
            <i class="fs-4 bi-bootstrap"></i>
            <span class="ms-1 d-none d-sm-inline text-white">Logout</span></a
          >
        </li>
      </ul>
      <hr />
      <div>Bench Ease © {{ new Date().getFullYear() }}</div>
    </div>
  </aside>
</template>
