<script>
// Company_P04_p003
import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import PaginationNav from '@/components/ui/pagination/PaginationNav.vue';
import PaginationNavArrow from '@/components/ui/pagination/PaginationNavArrow.vue';
import PaginationNavEllipsis from '@/components/ui/pagination/PaginationNavEllipsis.vue';
import PaginationNavNumber from '@/components/ui/pagination/PaginationNavNumber.vue';
import TextButton from '@/components/ui/button/TextButton.vue';

import IconDownloadSmall from '@/assets/images/icon/download-small.svg?component';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageTitle,
    PaginationNav,
    PaginationNavArrow,
    PaginationNavEllipsis,
    PaginationNavNumber,
    TextButton,
    IconDownloadSmall,
  },
};
</script>

<template>
  <PageContents size="wide">
    <template v-slot:head>
      <LocationBar
        :data="[
          {
            text: '홈',
            to: '/main/home',
          },
          {
            text: '회사소개',
            to: '/',
          },
          {
            text: '투자정보',
          },
          {
            text: '경영공시',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageTitle>경영공시</PageTitle>
    </PageHead>

    <div>
      <div :class="$style['board']">
        <table>
          <colgroup>
            <col style="width: 67px" />
            <col />
            <col style="width: 117px" />
            <col style="width: 120px" />
          </colgroup>
          <tbody>
            <tr v-for="i in 10" :key="i">
              <td>
                <span :class="$style['board__num']">
                  {{ 101 - i }}
                </span>
              </td>
              <td>
                <a href="/foo/bar.pdf" download :class="$style['board__link']">
                  <span
                    :class="[
                      $style['board__title'],
                      $style['board__title--multi'],
                    ]"
                  >
                    게시물 제목 게시물 제목 게시물 제목 게시물 제목 게시물 제목
                    게시물 제목 게시물 제목 게시물 제목 게시물 제목 게시물 제목
                    게시물 제목 게시물 제목 게시물 제목 게시물 제목 게시물 제목
                    게시물 제목 게시물 제목 게시물 제목 게시물 제목 게시물 제목
                    게시물 제목 게시물 제목 게시물 제목 게시물 제목 게시물 제목
                  </span>
                </a>
              </td>
              <td>
                <div class="inline-wrap">
                  <TextButton
                    iconSize="large"
                    textSize="regular"
                    theme="quinary"
                    tagName="a"
                    href="/foo/bar.pdf"
                    download
                  >
                    <template v-slot:leftIcon>
                      <IconDownloadSmall />
                    </template>
                    다운로드
                  </TextButton>
                </div>
              </td>
              <td>2022.08.30</td>
            </tr>
          </tbody>
        </table>
      </div>

      <!-- Case : 첫번째 페이지일 때 -->
      <PaginationNav>
        <PaginationNavArrow type="prev" :disabled="true" />
        <PaginationNavNumber :active="true">1</PaginationNavNumber>
        <PaginationNavNumber>2</PaginationNavNumber>
        <PaginationNavNumber>3</PaginationNavNumber>
        <PaginationNavNumber>4</PaginationNavNumber>
        <PaginationNavNumber>5</PaginationNavNumber>
        <PaginationNavNumber>6</PaginationNavNumber>
        <PaginationNavNumber>7</PaginationNavNumber>
        <PaginationNavEllipsis />
        <PaginationNavNumber>999</PaginationNavNumber>
        <PaginationNavArrow type="next" />
      </PaginationNav>
      <!-- // Case : 첫번째 페이지일 때 -->

      <!-- Case : 중간 페이지일 때 -->
      <PaginationNav>
        <PaginationNavArrow type="prev" />
        <PaginationNavNumber>1</PaginationNavNumber>
        <PaginationNavEllipsis />
        <PaginationNavNumber>13</PaginationNavNumber>
        <PaginationNavNumber>14</PaginationNavNumber>
        <PaginationNavNumber :active="true">15</PaginationNavNumber>
        <PaginationNavNumber>16</PaginationNavNumber>
        <PaginationNavNumber>17</PaginationNavNumber>
        <PaginationNavEllipsis />
        <PaginationNavNumber>99</PaginationNavNumber>
        <PaginationNavArrow type="next" />
      </PaginationNav>
      <!-- // Case : 중간 페이지일 때 -->

      <!-- Case : 마지막 페이지일 때 -->
      <PaginationNav>
        <PaginationNavArrow type="prev" />
        <PaginationNavNumber>1</PaginationNavNumber>
        <PaginationNavEllipsis />
        <PaginationNavNumber>93</PaginationNavNumber>
        <PaginationNavNumber>94</PaginationNavNumber>
        <PaginationNavNumber>95</PaginationNavNumber>
        <PaginationNavNumber>96</PaginationNavNumber>
        <PaginationNavNumber>97</PaginationNavNumber>
        <PaginationNavNumber>98</PaginationNavNumber>
        <PaginationNavNumber :active="true">99</PaginationNavNumber>
        <PaginationNavArrow type="next" :disabled="true" />
      </PaginationNav>
      <!-- // Case : 마지막 페이지일 때 -->
    </div>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/company/Company_P04_p003.scss';
</style>
