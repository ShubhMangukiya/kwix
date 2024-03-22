<template>
  <div class="h-screen grid grid-cols-3 divide-x">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <div class="flex-1 overflow-y-auto p-8">
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
      </div>
      <div class="border-t bg-white flex items-center">
        <button
          @click="prefillDemoData"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Add demo data </span>
          <icon name="mdi:code-json" class="h-4 w-4" />
        </button>
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
        <a
          href="https://github.com/ShubhMangukiya/kwix"
          target="_blank"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Github </span>
          <icon name="mdi:github" class="h-4 w-4" />
        </a>
      </div>
    </div>
    <app-form-preview :data="data" />
  </div>
</template>

<script setup>
import { encodeData } from "../utils/transformer";
const data = ref({
  n: "",
  d: "",
  i: "",
  f: "",
  t: "",
  ig: "",
  gh: "",
  tg: "",
  l: "",
  e: "",
  w: "",
  y: "",
  ls: [],
});

const prefillDemoData = () => {
  data.value = {
    n: "Shubh Mangukiya",
    d: "I'm student of Parul University",
    i: "https://media.licdn.com/dms/image/D4D03AQEnIaHVnx4CQg/profile-displayphoto-shrink_800_800/0/1706432114697?e=2147483647&v=beta&t=bj1E4YMxCVBEVgrcpJINlTir69nmfH2eca1zdUO3NiM",
    f: "https://www.facebook.com/shubh.mangukiya.11",
    t: "https://twitter.com/shubhmangukiya_",
    ig: "https://www.instagram.com/shubhmangukiya_",
    e: "shubh.mangukiya01@gmail.com",
    gh: "https://github.com/ShubhMangukiya",
    tg: "https://t.me/shubhmangukiya",
    w: "+919099331142",
    y: "https://youtube.com/",
    l: "https://linkedin.com/in/shubhmangukiya",
    ls: [
      {
        l: "My Website",
        i: "ph:globe-duotone",
        u: "https://placea.in",
      },
      {
        l: "Amazon wishlist",
        i: "ant-design:amazon-outlined",
        u: "https://amazon.in",
      },
      {
        l: "React JS course",
        i: "grommet-icons:reactjs",
        u: "https://reactjs.org/",
      },
      {
        l: "Donate for our cause",
        i: "iconoir:donate",
        u: "https://who.int",
      },
      {
        l: "Download my resume",
        i: "ph:file-pdf",
        u: "https://google.com",
      },
    ],
  };
};

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};
</script>
