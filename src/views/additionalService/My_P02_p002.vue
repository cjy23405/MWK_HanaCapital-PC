<script>
// My_P02_p002
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import PageSubText from '@/components/ui/text/PageSubText.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import BasicHr from '@/components/ui/common/BasicHr.vue';
import CarEmblem from '@/components/ui/imageData/CarEmblem.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import RoundStatus from '@/components/ui/text/RoundStatus.vue';
import TextProgress from '@/components/ui/progress/TextProgress.vue';
import UiAccordion from '@/components/ui/accordion/UiAccordion.vue';
import UiAccordionItem from '@/components/ui/accordion/UiAccordionItem.vue';
import UiAccordionLayer from '@/components/ui/accordion/UiAccordionLayer.vue';
import UiAccordionOpener from '@/components/ui/accordion/UiAccordionOpener.vue';
import PaginationNav from '@/components/ui/pagination/PaginationNav.vue';
import PaginationNavArrow from '@/components/ui/pagination/PaginationNavArrow.vue';
import PaginationNavEllipsis from '@/components/ui/pagination/PaginationNavEllipsis.vue';
import PaginationNavNumber from '@/components/ui/pagination/PaginationNavNumber.vue';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageTitle,
    PageSubText,
    BasicBox,
    BasicHr,
    CarEmblem,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    RoundStatus,
    TextProgress,
    UiAccordion,
    UiAccordionItem,
    UiAccordionLayer,
    UiAccordionOpener,
    PaginationNav,
    PaginationNavArrow,
    PaginationNavEllipsis,
    PaginationNavNumber,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setActive(() => 'onlineBranch');
      store.ui.header.setDepthActive(() => 'onlineBranch001');
    });

    onUnmounted(() => {
      store.ui.header.setActive();
      store.ui.header.setDepthActive();
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
            text: '부가서비스',
          },
          {
            text: '진행상태조회',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageTitle>상담내역 및 진행단계를 확인해 주세요</PageTitle>
      <!-- Case : 상담내역이 있을경우 -->
      <PageSubText>
        자동차금융 상담 고객 전용 서비스입니다.<br />
        최근 4주 이내 상담 진행 내역만 확인 가능합니다.
      </PageSubText>
      <!-- //Case : 상담내역이 있을경우 -->
    </PageHead>

    <!-- Case : 상담내역이 없을경우 -->
    <div :class="$style['empty']">
      <p :class="$style['empty__text']">현재 진행중인 상담이 없습니다.</p>
    </div>
    <!-- //Case : 상담내역이 없을경우 -->

    <!-- Case : 상담내역이 있을경우 -->
    <div>
      <UiAccordion>
        <!-- Case : 접수 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >접수</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="0"
                />
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 접수 -->

        <!-- Case : 상담 및 심사 - 상담 및 심사중 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >상담 및 심사중</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="1"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    상담 및 심사가 진행 중에 있습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 상담 및 심사 - 상담 및 심사중 -->

        <!-- Case : 상담 및 심사 - 심사완료 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >심사완료</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="1"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    심사가 완료되었습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 상담 및 심사 - 심사완료 -->

        <!-- Case : 계약 - 계약준비중 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >계약준비중</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="2"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    계약 체결을 위해 준비 중에 있습니다.<br />
                    준비가 완료 되는대로, 계약 진행 예정입니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 계약 - 계약준비중 -->

        <!-- Case : 계약 - 계약진행중 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >계약진행중</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="2"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    계약이 진행 중에 있습니다.<br />
                    전자약정을 하시면 보다 빠른 진행이 가능합니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 계약 - 계약진행중 -->

        <!-- Case : 계약 - 계약완료 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >계약완료</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="2"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    계약 체결이 완료되었습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 계약 - 계약완료 -->

        <!-- Case : 계약 - 취소 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="nonary" size="large" :block="true"
                  >취소</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="2"
                  :disabled="true"
                />

                <div
                  :class="[
                    $style['inline-alert'],
                    $style['inline-alert--error'],
                    'row-margin-contents',
                  ]"
                >
                  <p :class="$style['inline-alert__text']">
                    계약이 취소되었습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 계약 - 취소 -->

        <!-- Case : 실행 - 차량출고중 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >차량출고중</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="3"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    차량 출고 중에 있습니다.<br />
                    차량 출고 및 등록이 완료 되는대로 고객님께 차량을 인도드릴
                    예정입니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 실행 - 차량출고중 -->

        <!-- Case : 실행 - 완료 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="undenary" size="large" :block="true"
                  >완료</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="3"
                />

                <div :class="[$style['inline-alert'], 'row-margin-contents']">
                  <p :class="$style['inline-alert__text']">
                    차량 출고가 완료되었습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 실행 - 완료 -->

        <!-- Case : 실행 - 취소 -->
        <UiAccordionItem :classNames="{ item: 'row-margin-contents' }">
          <BasicBox>
            <div class="flex-box">
              <div class="flex-box__cell flex-1">
                <div class="flex-box row-margin-small">
                  <div class="flex-box__cell">
                    <CarEmblem
                      src="/images/_dummy/car-emblem.png"
                      name="현대"
                    />
                  </div>
                  <div class="flex-box__cell flex-box__cell--small">
                    <p class="text-body-4 font-weight-light">2020년식</p>
                  </div>
                </div>
                <h3 class="text-title-2 font-weight-medium">오토리스</h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  쏘나타 뉴 라이즈 1.6T-Gdi 스마트 (마이 스마트 핏)
                </p>
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <RoundStatus theme="nonary" size="large" :block="true"
                  >취소</RoundStatus
                >
              </div>
              <div class="flex-box__cell flex-box__cell--medium-regular">
                <UiAccordionOpener />
              </div>
            </div>

            <BasicHr theme="quaternary" className="row-margin-contents" />

            <UiAccordionLayer>
              <div :class="$style['contents']">
                <TextProgress
                  :steps="['접수', '상담 및 심사', '계약', '실행']"
                  :current="3"
                  :disabled="true"
                />

                <div
                  :class="[
                    $style['inline-alert'],
                    $style['inline-alert--error'],
                    'row-margin-contents',
                  ]"
                >
                  <p :class="$style['inline-alert__text']">
                    계약이 취소되었습니다.
                  </p>
                </div>
              </div>
            </UiAccordionLayer>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>상담번호</KeyValueTitle>
                <KeyValueText>7894561234567</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청일자</KeyValueTitle>
                <KeyValueText>2022.12.26</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>신청금액</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>승인한도</KeyValueTitle>
                <KeyValueText>24,990,000 원</KeyValueText>
              </KeyValueItem>
            </KeyValue>
          </BasicBox>
        </UiAccordionItem>
        <!-- // Case : 실행 - 취소 -->
      </UiAccordion>

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
    <!-- //Case : 상담내역이 있을경우 -->
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/additionalService/My_P02_p002.scss';
</style>
