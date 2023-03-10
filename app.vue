<template>
  <div>
    <div class="common-layout">
      <el-container class="min-h-screen">
        <el-aside width="auto" class="border-r-[1px] border-r-gray-300 p-4">
          <SideBar />
        </el-aside>
        <el-container class="flex max-h-[100vh]">
          <el-header height="auto"><Header title="Installations" /></el-header>
          <el-main
            style="overflow: hidden; display: flex; flex-direction: column"
            ><NuxtPage
          /></el-main>
          <el-footer height="auto"><Footer /></el-footer>
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
