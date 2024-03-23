<template>
  <header
    class="h-full w-full justify-between flex items-center px-5 border-b dark:border-slate-600 bg-white dark:bg-slate-900 max-h-20"
  >
    <div class="max-w-60 h-full w-full items-center flex">
      <div @click="toggleSidebar" class="cursor-pointer lg:hidden">
        <Icon name="material-symbols:menu-rounded" class="text-2xl mr-4" />
      </div>
      <h2 class="text-slate-800 font-bold text-xl uppercase">Testing Repo</h2>
    </div>
    <div class="w-fit">
      <div
        class="flex gap-5 text-slate-500 dark:text-slate-400 justify-center items-center pr-5"
      >
        <DropdownMenu>
          <DropdownMenuTrigger>
            <Avatar class="h-8 w-8">
              <AvatarImage
                src="https://a.storyblok.com/f/191576/1200x800/faa88c639f/round_profil_picture_before_.webp"
                alt="@radix-vue"
              />
              <AvatarFallback>CN</AvatarFallback>
            </Avatar>
          </DropdownMenuTrigger>
          <DropdownMenuContent class="w-48 mr-8">
            <DropdownMenuLabel>My Account</DropdownMenuLabel>
            <DropdownMenuSeparator />
            <DropdownMenuGroup>
              <DropdownMenuItem>
                <Icon
                  name="material-symbols:person-rounded"
                  class="text-xl mr-2"
                />
                <span class="font-normal">Profile</span>
              </DropdownMenuItem>
              <DropdownMenuItem>
                <Icon
                  name="material-symbols:settings-rounded"
                  class="text-xl mr-2"
                />
                <span>Settings</span>
              </DropdownMenuItem>
              <DropdownMenuSeparator />
              <DropdownMenuItem @click="logout" class="cursor-pointer">
                <Icon name="material-symbols:logout" class="text-xl mr-2" />
                <span>Logout</span>
              </DropdownMenuItem>
            </DropdownMenuGroup>
          </DropdownMenuContent>
        </DropdownMenu>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
defineProps(["toggleSidebar"]);

const router = useRouter();

const logout = () => {
  router.push("/login");
};
</script>
