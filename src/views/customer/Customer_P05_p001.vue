<script>
// Customer_P05_p001
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import BasicSelect from '@/components/ui/form/BasicSelect.vue';
import PaginationNav from '@/components/ui/pagination/PaginationNav.vue';
import PaginationNavArrow from '@/components/ui/pagination/PaginationNavArrow.vue';
import PaginationNavEllipsis from '@/components/ui/pagination/PaginationNavEllipsis.vue';
import PaginationNavNumber from '@/components/ui/pagination/PaginationNavNumber.vue';
import TextButton from '@/components/ui/button/TextButton.vue';

import IconMap from '@/assets/images/icon/map.svg?component';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageTitle,
    InputBlock,
    InputBlockCell,
    BasicSelect,
    PaginationNav,
    PaginationNavArrow,
    PaginationNavEllipsis,
    PaginationNavNumber,
    TextButton,
    IconMap,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setActive(() => 'customer');
    });

    onUnmounted(() => {
      store.ui.header.setActive();
    });
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
            text: '고객센터',
            to: '/',
          },
          {
            text: '지점안내',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageTitle>지점안내</PageTitle>
    </PageHead>

    <div :class="$style['board-search-bar']">
      <InputBlock>
        <InputBlockCell :flexible="true">
          <BasicSelect
            :options="[
              {
                value: '1',
                label: '전체',
              },
              {
                value: '2',
                label: '서울',
              },
              {
                value: '3',
                label: '경기',
              },
              {
                value: '4',
                label: '강원',
              },
              {
                value: '5',
                label: '충청',
              },
              {
                value: '6',
                label: '경상',
              },
              {
                value: '7',
                label: '전라',
              },
              {
                value: '8',
                label: '제주',
              },
            ]"
            title="지역 선택"
            defaultValue="1"
          />
        </InputBlockCell>
      </InputBlock>
    </div>

    <div class="flex-box align-items-start">
      <div class="flex-box__cell flex-1">
        <div :class="$style['board']">
          <table>
            <colgroup>
              <col style="width: 140px" />
              <col />
              <col style="width: 140px" />
            </colgroup>
            <tbody>
              <tr>
                <td class="align-left">본사</td>
                <td class="align-left color-black">
                  서울 강남구 테헤란로 127 하나금융그룹 (역삼동, 강남사옥)
                </td>
                <td>
                  <!-- Case : 선택 되었을 때 theme="secondary" -->
                  <TextButton
                    :iconFillAll="true"
                    iconSize="large"
                    textSize="regular"
                    theme="secondary"
                  >
                    <template v-slot:leftIcon>
                      <IconMap />
                    </template>
                    지도보기
                  </TextButton>
                </td>
              </tr>
              <tr v-for="i in 4" :key="i">
                <td class="align-left">경수중고차센터(안산SI)</td>
                <td class="align-left color-black">
                  서울 강남구 테헤란로 127 하나금융그룹 (역삼동, 강남사옥)
                </td>
                <td>
                  <TextButton
                    :iconFillAll="true"
                    iconSize="large"
                    textSize="regular"
                    theme="quinary"
                  >
                    <template v-slot:leftIcon>
                      <IconMap />
                    </template>
                    지도보기
                  </TextButton>
                </td>
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

      <div class="flex-box__cell flex-box__cell--large flex-1">
        <div :class="$style['map-area']">
          <div style="height: 100%; background-color: #f7f7f7">
            // 지도 영역
          </div>
        </div>
      </div>
    </div>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/customer/Customer_P05_p001.scss';
</style>
