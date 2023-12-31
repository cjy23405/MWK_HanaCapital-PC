<script>
// My_p05_p002
import { reactive, onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import LocationBar from '@/components/ui/layout/LocationBar.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageHeadRow from '@/components/ui/text/PageHeadRow.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import BoxCheck from '@/components/ui/form/BoxCheck.vue';
import BoxCheckLabel from '@/components/ui/form/BoxCheckLabel.vue';
import BoxCheckList from '@/components/ui/form/BoxCheckList.vue';
import BoxCheckListItem from '@/components/ui/form/BoxCheckListItem.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';
import NoticeText from '@/components/ui/text/NoticeText.vue';
import BasicBoxHead from '@/components/ui/common/BasicBoxHead.vue';
import BasicBoxHeadLeft from '@/components/ui/common/BasicBoxHeadLeft.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import RadioButton from '@/components/ui/form/RadioButton.vue';
import RadioButtonObject from '@/components/ui/form/RadioButtonObject.vue';
import RadioButtonLabelText from '@/components/ui/form/RadioButtonLabelText.vue';

export default {
  components: {
    PageContents,
    LocationBar,
    PageHead,
    PageHeadRow,
    PageTitle,
    PageMainText,
    StepProgress,
    BoxCheck,
    BoxCheckLabel,
    BoxCheckList,
    BoxCheckListItem,
    BasicButton,
    ButtonList,
    ButtonListItem,
    NoticeText,
    BasicBox,
    BasicBoxHead,
    BasicBoxHeadLeft,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    RadioButton,
    RadioButtonObject,
    RadioButtonLabelText,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    const state = reactive({
      details001Error: false,
      details002Error: false,
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
            text: '온라인 지점',
            to: '/',
          },
          {
            text: '계약정보',
          },
          {
            text: '금리인하요구권 신청',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageHeadRow>
        <PageTitle align="left">금리인하요구권 신청</PageTitle>
        <template v-slot:right>
          <StepProgress :total="4" :current="1" />
        </template>
      </PageHeadRow>
      <PageMainText align="left">
        금리인하요구권 신청서를 작성해 주세요
      </PageMainText>
    </PageHead>

    <div>
      <section class="row-margin-block-small">
        <h3 class="text-title-1 row-margin-contents">대상 여신 내용</h3>

        <BasicBox>
          <BasicBoxHead>
            <BasicBoxHeadLeft>
              <h3 class="text-title-2 font-weight-medium">오토론</h3>
            </BasicBoxHeadLeft>
          </BasicBoxHead>

          <KeyValue :wrap="true">
            <KeyValueItem>
              <KeyValueTitle>대출금액</KeyValueTitle>
              <KeyValueText>81,310,000 원</KeyValueText>
            </KeyValueItem>

            <KeyValueItem>
              <KeyValueTitle>적용금리</KeyValueTitle>
              <KeyValueText>4,709%</KeyValueText>
            </KeyValueItem>

            <KeyValueItem>
              <KeyValueTitle>대출실행일</KeyValueTitle>
              <KeyValueText>2021.12.31</KeyValueText>
            </KeyValueItem>

            <KeyValueItem>
              <KeyValueTitle>대출종료일</KeyValueTitle>
              <KeyValueText>2026.12.21</KeyValueText>
            </KeyValueItem>
          </KeyValue>
        </BasicBox>
      </section>

      <section class="row-margin-block-small">
        <h3 class="text-title-1 row-margin-contents">신청사유</h3>

        <BoxCheckList>
          <BoxCheckListItem>
            <BoxCheck
              name="My_p05_p002_method"
              id="My_p05_p002_method_001"
              :defaultChecked="true"
            >
              <BoxCheckLabel>신용도 상승</BoxCheckLabel>
            </BoxCheck>
          </BoxCheckListItem>
          <BoxCheckListItem>
            <BoxCheck name="My_p05_p002_method" id="My_p05_p002_method_002">
              <BoxCheckLabel>소득 재산 증가</BoxCheckLabel>
            </BoxCheck>
          </BoxCheckListItem>
          <BoxCheckListItem>
            <BoxCheck name="My_p05_p002_method" id="My_p05_p002_method_003">
              <BoxCheckLabel>기타</BoxCheckLabel>
            </BoxCheck>
          </BoxCheckListItem>
        </BoxCheckList>

        <!-- Case : 신용도 상승 선택 시 노출 -->
        <div :class="[$style['check-list'], 'row-margin-contents']">
          <ul :class="$style['check-list__list']">
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details001"
                id="My_p05_p002_details001_001"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>신용평점(등급) 개선</RadioButtonLabelText>
              </RadioButton>
            </li>
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details001"
                id="My_p05_p002_details001_002"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>재무상태 개선</RadioButtonLabelText>
              </RadioButton>
            </li>
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details001"
                id="My_p05_p002_details001_003"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>기타 신용도 상승</RadioButtonLabelText>
              </RadioButton>
            </li>
          </ul>
        </div>
        <!-- // Case : 신용도 상승 선택 시 노출 -->

        <!-- Case : 소득 재산 증가 선택 시 노출 -->
        <div :class="[$style['check-list'], 'row-margin-contents']">
          <ul :class="$style['check-list__list']">
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details002"
                id="My_p05_p002_details002_001"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>소득증가</RadioButtonLabelText>
              </RadioButton>
            </li>
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details002"
                id="My_p05_p002_details002_002"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>재산증가</RadioButtonLabelText>
              </RadioButton>
            </li>
            <li :class="$style['check-list__item']">
              <RadioButton
                name="My_p05_p002_details002"
                id="My_p05_p002_details002_003"
              >
                <RadioButtonObject />
                <RadioButtonLabelText>기타 소득증가</RadioButtonLabelText>
              </RadioButton>
            </li>
          </ul>
        </div>
        <!-- // Case : 소득 재산 증가 선택 시 노출 -->
      </section>

      <section class="row-margin-block-small">
        <h3 class="text-title-1 row-margin-small">제출서류</h3>
        <p class="text-body-1 font-weight-light color-gray-secondary">
          제출 가능한 항목을 선택해 주세요.
        </p>

        <div class="row-margin-contents">
          <BoxCheckList :wrap="true">
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_001"
              >
                <BoxCheckLabel>없음</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_002"
              >
                <BoxCheckLabel>건강보험 자격득실/납부확인서</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_003"
              >
                <BoxCheckLabel>재직증명서</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_004"
              >
                <BoxCheckLabel>근로소득원천징수영수증</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_005"
              >
                <BoxCheckLabel>소득금액증명원</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_006"
              >
                <BoxCheckLabel>사업소득원천징수영수증</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_007"
              >
                <BoxCheckLabel>재무제표</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_008"
              >
                <BoxCheckLabel>부가가치세과세표준증명</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
            <BoxCheckListItem>
              <BoxCheck
                :minSide="true"
                name="My_p05_p002_submission"
                id="My_p05_p002_submission_009"
              >
                <BoxCheckLabel>기타</BoxCheckLabel>
              </BoxCheck>
            </BoxCheckListItem>
          </BoxCheckList>

          <NoticeText :classNames="{ wrap: 'row-margin-item-medium' }">
            당사는 신청인의 신용상태 개선을 확인하기 위해 추가서류를 요청할 수
            있습니다.
          </NoticeText>
        </div>
      </section>

      <BasicBox theme="tertiary">
        <p class="text-body-1 color-gray font-weight-medium">
          본인은 상기 항목의 내용을 사실대로 기재하였고, 귀사의 신용평가
          시스템에 따른 결과에 이의를 제기하지 않겠습니다.
        </p>
      </BasicBox>

      <div class="row-margin-contents align-right">
        <p class="text-body-1 color-gray font-weight-medium">
          위 내역이 사실과 다름이 없음을 확인합니다.
        </p>
        <p
          class="text-body-1 color-gray-tertiary font-weight-light row-margin-contents-small"
        >
          2023년 01월 05일
        </p>
      </div>
    </div>

    <ButtonList>
      <ButtonListItem>
        <BasicButton>다음</BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/onlineBranch/My_p05_p002.scss';
</style>
