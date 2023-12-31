<script>
// AF_P06_p002
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageHeadRow from '@/components/ui/text/PageHeadRow.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import BasicInput from '@/components/ui/form/BasicInput.vue';
import SearchButton from '@/components/ui/button/SearchButton.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import BasicBoxHead from '@/components/ui/common/BasicBoxHead.vue';
import BasicBoxHeadLeft from '@/components/ui/common/BasicBoxHeadLeft.vue';
import UnitText from '@/components/ui/text/UnitText.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import TextButton from '@/components/ui/button/TextButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import CarEmblem from '@/components/ui/imageData/CarEmblem.vue';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageTitle,
    PageHeadRow,
    StepProgress,
    PageMainText,
    InputBlock,
    InputBlockCell,
    BasicInput,
    SearchButton,
    BasicBox,
    BasicBoxHead,
    BasicBoxHeadLeft,
    UnitText,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    TextButton,
    ButtonList,
    ButtonListItem,
    BasicButton,
    CarEmblem,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setActive(() => 'auto');
    });

    onUnmounted(() => {
      store.ui.header.setActive();
    });
  },
};
</script>

<template>
  <PageContents>
    <template v-slot:head>
      <LocationBar
        :data="[
          {
            text: '홈',
            to: '/main/home',
          },
          {
            text: '오토금융',
            to: '/',
          },
          {
            text: '중고차오토론',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageHeadRow>
        <PageTitle align="left">중고차오토론</PageTitle>
        <template v-slot:right>
          <StepProgress :total="4" :current="1" />
        </template>
      </PageHeadRow>
      <PageMainText align="left">차량번호를 입력해 주세요</PageMainText>
    </PageHead>

    <InputBlock>
      <InputBlockCell :flexible="true">
        <BasicInput type="search" title="차량번호" placeholder="차량번호" />
      </InputBlockCell>
      <InputBlockCell type="search">
        <SearchButton />
      </InputBlockCell>
    </InputBlock>

    <section class="contents-wrap row-margin-block row-margin-bottom-none">
      <h3 class="text-title-1 row-margin-contents">차량정보</h3>

      <!-- Case : 승계 가능한 차량이 없을 경우 -->
      <div :class="$style['empty']">
        <p :class="$style['empty__text']">
          승계 가능한 차량이 없습니다.<br />
          양도인에게 승계 동의를 요청해 주세요.
        </p>
      </div>
      <!-- // Case : 승계 가능한 차량이 없을 경우 -->

      <!-- Case : 승계 가능한 차량이 있을 경우 -->
      <BasicBox>
        <BasicBoxHead>
          <BasicBoxHeadLeft>
            <div class="flex-box row-margin-small">
              <div class="flex-box__cell">
                <CarEmblem src="/images/_dummy/car-emblem.png" name="현대" />
              </div>
              <div class="flex-box__cell flex-box__cell--small">
                <p class="text-body-4 font-weight-light">2020년식</p>
              </div>
            </div>
            <h4 class="text-title-2 font-weight-medium">
              쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
            </h4>
            <div class="row-margin-item">
              <UnitText rightUnit="원"><strong>23,500,000</strong></UnitText>
            </div>
          </BasicBoxHeadLeft>
        </BasicBoxHead>
        <KeyValue :wrap="true">
          <KeyValueItem>
            <KeyValueTitle>주행거리</KeyValueTitle>
            <KeyValueText>65,000 Km</KeyValueText>
          </KeyValueItem>
          <KeyValueItem>
            <KeyValueTitle>사고유무</KeyValueTitle>
            <KeyValueText>
              <div class="flex-box">
                <div class="flex-box__cell flex-1">Y</div>
                <div class="flex-box__cell">
                  <TextButton
                    theme="secondary"
                    :underline="true"
                    textSize="regular"
                    :block="true"
                  >
                    세부이력
                  </TextButton>
                </div>
              </div>
            </KeyValueText>
          </KeyValueItem>
        </KeyValue>
      </BasicBox>
      <!-- // Case : 승계 가능한 차량이 있을 경우 -->
    </section>

    <ButtonList>
      <ButtonListItem>
        <BasicButton>다음</BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/auto/AF_P06_p002.scss';
</style>
