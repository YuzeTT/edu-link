<script setup lang="ts">
// const name = $ref('')

// const router = useRouter()
// const go = () => {
//   if (name)
//     router.push(`/hi/${encodeURIComponent(name)}`)
// }

const links: { icon: string;text: string;show_url: string;url: string; bg_color?: string }[] = [
  { icon: 'i-carbon-smoothing', text: '教育部官网', show_url: 'www.moe.gov.cn', url: 'http://www.moe.gov.cn/', bg_color: 'bg-blue-500' },
  { icon: 'i-carbon-recording', text: '聚焦“双减”', show_url: 'www.moe.gov.cn/jyb_xwfb/moe_2082/2021/2021_zl53', url: 'http://www.moe.gov.cn/jyb_xwfb/moe_2082/2021/2021_zl53/', bg_color: 'bg-blue-500' },
  { icon: 'i-carbon-chart-custom', text: '投诉举报（匿名）', show_url: 'hudong.moe.gov.cn/zxjb/jbxz.jsp', url: 'https://hudong.moe.gov.cn/zxjb/jbxz.jsp' },
  { icon: 'i-carbon-email', text: '部长信箱', show_url: 'hudong.moe.gov.cn/bzxx', url: 'https://hudong.moe.gov.cn/bzxx/' },
]

// const links_fujian: { icon: string;text: string;url: string; bg_color?: string }[] = [
//   { icon: 'i-carbon-smoothing', text: '福建省人民政府', url: 'hhttps://www.fujian.gov.cn/hdjl/zxts/', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '福州市', url: 'http://fz12345.fuzhou.gov.cn/fzwp/regCallStep2.jsp', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '厦门市', url: 'http://www.xm12345.gov.cn', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '泉州市', url: 'http://qz12345.fujian.gov.cn/writeCall.jsp?callKind=1', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '三明市', url: 'https://12345.sm.gov.cn/12345/public/appeal/commonAppeal.jsp?type=complaint&loginflag=false', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '莆田市', url: 'http://www.putian.gov.cn/pt12345/webEditRequestStep1.jsp?callKind=1', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '南平市', url: 'http://np12345.fujian.gov.cn/writeCall.jsp?callKind=1', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '龙岩市', url: 'http://12345.longyan.gov.cn/portal12345/public/appeal/commonAppeal.jsp?type=complaint&loginflag=false', bg_color: 'bg-blue-500' },
//   { icon: 'i-carbon-recording', text: '宁德市', url: 'http://nd12345.fujian.gov.cn/writeCall.jsp?callKind=1', bg_color: 'bg-blue-500' },
// ]
const links_12345: { icon: string;text: string;url: string; bg_color?: string }[] = [
  { icon: 'i-carbon-smoothing', text: '福建省人民政府', url: 'https://www.fujian.gov.cn/hdjl/zxts/wyts/', bg_color: 'bg-blue-500' },
]

const phones: { text: string; phone: string }[] = [
  { text: '政务服务便民热线', phone: '12345' },
  { text: '教育部举报电话', phone: '010-66093315' },
]

const word: { title: string;text: string }[] = [
  { title: '当前热点', text: '双减' },
  { title: '热门举报', text: '作业量' },
]

const call = (phone: string) => {
  const a = document.createElement('a')
  a.href = `tel:${phone}`
  a.click()
}
</script>

<template>
  <div max-w-md mx-auto>
    <Card>
      <div flex items-center gap-3 p-5>
        <div h-15 w-15 bg-zinc-100 dark:bg-zinc-700 rounded-full flex items-center justify-center>
          <div i-carbon-rule inline-block text-2xl text-blue-700 dark:text-white />
        </div>
        <div>
          <div font-black text-zinc-800 dark:text-white text-lg>
            中国教育部门网站导航
          </div>
          <div text-zinc-500 text-lg dark:text-zinc-400>
            新增违反“双减”政策投诉板块
          </div>
        </div>
      </div>
      <div p-5>
        <div grid grid-cols-2 gap-3>
          <div v-for="(item, i) in word" :key="i" text-center>
            <div font-bold text-lg text-zinc-500 pb-1>
              {{ item.title }}
            </div>
            <div font-black text-2xl text-zinc-800>
              {{ item.text }}
            </div>
          </div>
        </div>
      </div>
    </Card>
    <div my-8 />
    <Card>
      <div px-5 py-3 flex items-center gap-2>
        <div i-carbon-circle-dash text-zinc-400 />
        <div font-black text-zinc-800 dark:text-white text-lg>
          公告
        </div>
      </div>
      <div p-5>
        <div text-red>
          纪检监察机关应当建立健全检举控告保密制度，严格落实保密要求！
        </div>
        <div>优先选择省级举报</div>
      </div>
    </Card>
    <div my-8 />
    <Card>
      <div px-5 py-3 flex items-center gap-2>
        <div i-carbon-circle-dash text-zinc-400 />
        <div font-black text-zinc-800 dark:text-white text-lg>
          快捷链接
        </div>
      </div>
      <div p-5 grid grid-cols-2 gap-2>
        <div v-for="(item, i) in links" :key="i" border-2 border-zinc-100 hover:border-blue-500 transition p-3 rounded-lg dark:border-zinc-700>
          <div h-12 w-12 rounded-full flex items-center justify-center mb-3 :class="item.bg_color ? item.bg_color : 'bg-gray-100 dark:bg-zinc-700'">
            <div :class="[item.icon, item.bg_color ? 'text-white' : 'text-zinc-500 ']" inline-block text-2xl dark="text-white" />
          </div>
          <div font-black text-zinc-700 text-lg dark:text-white>
            {{ item.text }}
          </div>
          <div text-zinc-400 truncate dark:text-zinc-500>
            {{ item.show_url }}
          </div>
        </div>
      </div>
    </Card>
    <div my-8 />
    <Card>
      <div px-5 py-3 flex items-center gap-2>
        <div i-carbon-circle-dash text-zinc-400 />
        <div font-black text-zinc-800 text-lg dark:text-white>
          相关热线
        </div>
      </div>
      <div p-5 space-y-5>
        <div v-for="(item, i) in phones" :key="i" flex justify-between items-center>
          <div flex items-center gap-3>
            <div i-carbon-phone-filled text-2xl />
            <div>
              <div font-black text-zinc-700 text-lg dark:text-white>
                {{ item.text }}
              </div>
              <div font-black text-zinc-500 text-md dark:text-zinc-400>
                {{ item.phone }}
              </div>
            </div>
          </div>
          <!-- <div h-12 w-12 rounded-full flex items-center justify-center mb-3 bg-gray-100>
            <div text-zinc-500 i-carbon-send inline-block text-2xl />
          </div> -->
          <button bg-blue-100 font-bold text-lg px-4 py-1 text-blue-500 rounded-full hover="bg-blue-500 text-white" transition @click="call(item.phone)">
            拨打
          </button>
          <!-- <div text-2xl i-carbon- /> -->
        </div>
      </div>
    </Card>
    <div my-8 />
    <Card>
      <div px-5 py-3 flex items-center gap-2>
        <div i-carbon-circle-dash text-zinc-400 />
        <div font-black text-zinc-800 text-lg dark:text-white>
          省级在线投诉
        </div>
      </div>
      <div p-5 grid grid-cols-2 gap-2>
        <div v-for="(item, i) in links_12345" :key="i" border-2 border-zinc-100 hover:border-blue-500 transition p-3 rounded-lg dark:border-zinc-700>
          <div h-12 w-12 rounded-full flex items-center justify-center mb-3 :class="item.bg_color ? item.bg_color : 'bg-gray-100 dark:bg-zinc-700'">
            <div :class="[item.icon, item.bg_color ? 'text-white' : 'text-zinc-500 ']" inline-block text-2xl dark="text-white" />
          </div>
          <div font-black text-zinc-700 text-lg dark:text-white>
            {{ item.text }}
          </div>
        </div>
      </div>
    </Card>
  </div>
</template>
