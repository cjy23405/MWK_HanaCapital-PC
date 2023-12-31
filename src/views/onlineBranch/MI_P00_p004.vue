<script>
// MI_P00_p004
import { reactive, onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageHeadRow from '@/components/ui/text/PageHeadRow.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import BasicBoxHead from '@/components/ui/common/BasicBoxHead.vue';
import BasicBoxHeadLeft from '@/components/ui/common/BasicBoxHeadLeft.vue';
import BasicBoxHeadRight from '@/components/ui/common/BasicBoxHeadRight.vue';
import RoundStatus from '@/components/ui/text/RoundStatus.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import TextButton from '@/components/ui/button/TextButton.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import FormList from '@/components/ui/form/FormList.vue';
import FormListItem from '@/components/ui/form/FormListItem.vue';
import FormInvalid from '@/components/ui/form/FormInvalid.vue';
import FormInvalidMessage from '@/components/ui/form/FormInvalidMessage.vue';
import BasicSelect from '@/components/ui/form/BasicSelect.vue';
import PaginationNav from '@/components/ui/pagination/PaginationNav.vue';
import PaginationNavArrow from '@/components/ui/pagination/PaginationNavArrow.vue';
import PaginationNavEllipsis from '@/components/ui/pagination/PaginationNavEllipsis.vue';
import PaginationNavNumber from '@/components/ui/pagination/PaginationNavNumber.vue';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageHeadRow,
    PageTitle,
    PageMainText,
    StepProgress,
    BasicButton,
    ButtonList,
    ButtonListItem,
    BasicBox,
    BasicBoxHead,
    BasicBoxHeadLeft,
    BasicBoxHeadRight,
    RoundStatus,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    TextButton,
    InputBlock,
    InputBlockCell,
    FormList,
    FormListItem,
    FormInvalid,
    FormInvalidMessage,
    BasicSelect,
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

    const state = reactive({
      billingMethodError: [false, false, false, false, false],
      addressError: [false, false, false, false, false],
      emailError: [false, false, false, false, false],
    });

    onMounted(() => {
      store.ui.header.setActive(() => 'onlineBranch');
    });

    onUnmounted(() => {
      store.ui.header.setActive();
    });

    return {
      state,
    };
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
            text: '온라인지점',
            to: '/',
          },
          {
            text: '계약정보',
          },
          {
            text: '청구 방법/청구지 변경',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageHeadRow>
        <PageTitle align="left">청구 방법/청구지 변경</PageTitle>
        <template v-slot:right>
          <StepProgress :total="3" :current="1" />
        </template>
      </PageHeadRow>
      <PageMainText align="left">
        청구 방법/청구지를 변경해 주세요
      </PageMainText>
    </PageHead>

    <ul
      :class="[
        $style['basic-list'],
        $style['basic-list--regular'],
        $style['basic-list--regular-margin'],
      ]"
    >
      <li :class="[$style['basic-list__item'], 'font-weight-regular']">
        <div :class="$style['basic-list__symbol']"></div>
        <div :class="$style['basic-list__content']">
          청구 방법 및 청구지를 변경할 수 있습니다.
        </div>
      </li>
      <li :class="[$style['basic-list__item'], 'font-weight-regular']">
        <div :class="$style['basic-list__symbol']"></div>
        <div :class="$style['basic-list__content']">
          <div class="flex-box">
            <div class="flex-box__cell flex-1">
              청구지에 대한 주소 변경을 원하실 경우, [온라인지점 > 내정보관리]
              메뉴를 이용하세요.
            </div>
            <div class="flex-box__cell flex-box__cell--medium">
              <TextButton
                textSize="regular"
                theme="secondary"
                :underline="true"
                :block="true"
                :classNames="{ wrap: $style['right-button'] }"
              >
                바로가기
              </TextButton>
            </div>
          </div>
        </div>
      </li>
      <li :class="[$style['basic-list__item'], 'font-weight-regular']">
        <div :class="$style['basic-list__symbol']"></div>
        <div :class="$style['basic-list__content']">
          스탁론은 변경이 불가하며 고객센터(1800-1110)로 연락 바랍니다.
        </div>
      </li>
    </ul>

    <div class="row-margin-block-small row-margin-bottom-none">
      <ul class="reset-list">
        <!-- Case : 연체 -->
        <li class="row-margin-contents">
          <BasicBox>
            <BasicBoxHead>
              <BasicBoxHeadLeft>
                <h3 class="text-title-2 font-weight-medium">
                  오토리스 20고5678
                </h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  BMW 435d
                </p>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  L99999999999999
                </p>
              </BasicBoxHeadLeft>
              <BasicBoxHeadRight>
                <RoundStatus theme="nonary" size="large" :block="true">
                  연체
                </RoundStatus>
              </BasicBoxHeadRight>
            </BasicBoxHead>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>대출금액</KeyValueTitle>
                <KeyValueText>6,265,200 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>대출기간</KeyValueTitle>
                <KeyValueText>2021.02.02 ~ 2022.02.02</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>결제일</KeyValueTitle>
                <KeyValueText>05일</KeyValueText>
              </KeyValueItem>
            </KeyValue>

            <BasicBox theme="tertiary" className="row-margin-contents">
              <FormList>
                <FormListItem
                  titleText="청구방법"
                  target="#MI_P00_p004_billingMethod_0"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.billingMethodError[0]">
                    <InputBlock :error="state.billingMethodError[0]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label: '미발송',
                            },
                            {
                              value: '2',
                              label: '온라인(SMS)',
                            },
                            {
                              value: '3',
                              label: '우편',
                            },
                            {
                              value: '4',
                              label: '이메일',
                            },
                            {
                              value: '5',
                              label: '우편+이메일',
                            },
                            {
                              value: '6',
                              label: '우편(지속)',
                            },
                            {
                              value: '7',
                              label: '우편(지속)+이메일',
                            },
                          ]"
                          title="청구방법"
                          inputId="MI_P00_p004_billingMethod_0"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>

                <!-- Case : 우편 + 이메일, 우편(지속), 우편(지속)+이메일 선택 시 노출  -->
                <!-- Case : 청구방법 우편 선택 시 노출  -->
                <FormListItem
                  titleText="청구지주소"
                  target="#MI_P00_p004_address_0"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.addressError[0]">
                    <InputBlock :error="state.addressError[0]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label:
                                '사업장1 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                            {
                              value: '2',
                              label:
                                '사업장2 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                            {
                              value: '3',
                              label:
                                '사업장3 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                          ]"
                          title="청구지주소"
                          inputId="MI_P00_p004_address_0"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>
                <!-- // Case : 청구방법 우편 선택 시 노출  -->

                <!-- Case : 청구방법 이메일 선택 시 노출  -->
                <FormListItem
                  titleText="이메일주소"
                  target="#MI_P00_p004_email_0"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.emailError[0]">
                    <InputBlock :error="state.emailError[0]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label: 'test1@test.com',
                            },
                            {
                              value: '2',
                              label: 'test2@test.com',
                            },
                            {
                              value: '3',
                              label: 'test3@test.com',
                            },
                          ]"
                          title="이메일주소"
                          inputId="MI_P00_p004_email_0"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>
                <!-- // Case : 청구방법 이메일 선택 시 노출  -->
                <!-- // Case : 우편 + 이메일, 우편(지속), 우편(지속)+이메일 선택 시 노출  -->
              </FormList>
            </BasicBox>
          </BasicBox>
        </li>
        <!-- // Case : 연체 -->

        <li v-for="i in 4" :key="i" class="row-margin-contents">
          <BasicBox>
            <BasicBoxHead>
              <BasicBoxHeadLeft>
                <h3 class="text-title-2 font-weight-medium">
                  오토리스 20고5678
                </h3>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  BMW 435d
                </p>
                <p
                  class="text-body-3 color-gray-tertiary row-margin-item-small"
                >
                  L99999999999999
                </p>
              </BasicBoxHeadLeft>
            </BasicBoxHead>

            <KeyValue :wrap="true">
              <KeyValueItem>
                <KeyValueTitle>대출금액</KeyValueTitle>
                <KeyValueText>6,265,200 원</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>대출기간</KeyValueTitle>
                <KeyValueText>2021.02.02 ~ 2022.02.02</KeyValueText>
              </KeyValueItem>

              <KeyValueItem>
                <KeyValueTitle>결제일</KeyValueTitle>
                <KeyValueText>05일</KeyValueText>
              </KeyValueItem>
            </KeyValue>

            <BasicBox theme="tertiary" className="row-margin-contents">
              <FormList>
                <FormListItem
                  titleText="청구방법"
                  :target="`#MI_P00_p004_billingMethod_${i}`"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.billingMethodError[i]">
                    <InputBlock :error="state.billingMethodError[i]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label: '미발송',
                            },
                            {
                              value: '2',
                              label: '온라인(SMS)',
                            },
                            {
                              value: '3',
                              label: '우편',
                            },
                            {
                              value: '4',
                              label: '이메일',
                            },
                            {
                              value: '5',
                              label: '우편+이메일',
                            },
                            {
                              value: '6',
                              label: '우편(지속)',
                            },
                            {
                              value: '7',
                              label: '우편(지속)+이메일',
                            },
                          ]"
                          title="청구방법"
                          :inputId="`MI_P00_p004_billingMethod_${i}`"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>

                <!-- Case : 우편 + 이메일, 우편(지속), 우편(지속)+이메일 선택 시 노출  -->
                <!-- Case : 청구방법 우편 선택 시 노출  -->
                <FormListItem
                  titleText="청구지주소"
                  :target="`#MI_P00_p004_address_${i}`"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.addressError[i]">
                    <InputBlock :error="state.addressError[i]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label:
                                '사업장1 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                            {
                              value: '2',
                              label:
                                '사업장2 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                            {
                              value: '3',
                              label:
                                '사업장3 (01000 인천 서구 에코로 181 하나금융 로비)',
                            },
                          ]"
                          title="청구지주소"
                          :inputId="`MI_P00_p004_address_${i}`"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>
                <!-- // Case : 청구방법 우편 선택 시 노출  -->

                <!-- Case : 청구방법 이메일 선택 시 노출  -->
                <FormListItem
                  titleText="이메일주소"
                  :target="`#MI_P00_p004_email_${i}`"
                  :selectOnly="true"
                >
                  <FormInvalid :error="state.emailError[i]">
                    <InputBlock :error="state.emailError[i]">
                      <InputBlockCell :flexible="true">
                        <BasicSelect
                          :options="[
                            {
                              value: '1',
                              label: 'test1@test.com',
                            },
                            {
                              value: '2',
                              label: 'test2@test.com',
                            },
                            {
                              value: '3',
                              label: 'test3@test.com',
                            },
                          ]"
                          title="이메일주소"
                          :inputId="`MI_P00_p004_email_${i}`"
                          defaultValue="1"
                        />
                      </InputBlockCell>
                    </InputBlock>
                    <FormInvalidMessage>Error Message</FormInvalidMessage>
                  </FormInvalid>
                </FormListItem>
                <!-- // Case : 청구방법 이메일 선택 시 노출  -->
                <!-- // Case : 우편 + 이메일, 우편(지속), 우편(지속)+이메일 선택 시 노출  -->
              </FormList>
            </BasicBox>
          </BasicBox>
        </li>
      </ul>

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

    <ButtonList>
      <ButtonListItem>
        <BasicButton>변경 신청</BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/onlineBranch/MI_P00_p004.scss';
</style>
