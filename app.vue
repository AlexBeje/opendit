<template>
  <div>
    <div class="common-layout">
      <el-container class="min-h-screen">
        <el-aside width="auto" class="border-r-[1px] border-r-gray-300 p-4">
          <SideBar />
        </el-aside>
        <el-container class="flex max-h-[100vh]">
          <el-header height="auto" class="flex-1"
            ><Header title="Installations"
          /></el-header>
          <el-main class="flex-1"><NuxtPage /></el-main>
          <el-footer height="auto" class="flex-1"><Footer /></el-footer>
        </el-container>
      </el-container>
    </div>
  </div>
</template>

<style scoped lang="scss">
.el-header,
.el-footer {
  padding: 0 !important;
}
</style>
