<script>
// IF_P03_p003
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageHeadRow from '@/components/ui/text/PageHeadRow.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import PageMainText from '@/components/ui/text/PageMainText.vue';
import StepProgress from '@/components/ui/progress/StepProgress.vue';
import BasicBox from '@/components/ui/common/BasicBox.vue';
import KeyValue from '@/components/ui/text/KeyValue.vue';
import KeyValueItem from '@/components/ui/text/KeyValueItem.vue';
import KeyValueTitle from '@/components/ui/text/KeyValueTitle.vue';
import KeyValueText from '@/components/ui/text/KeyValueText.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

export default {
  components: {
    PageContents,
    PageHead,
    PageHeadRow,
    PageTitle,
    PageMainText,
    StepProgress,
    BasicBox,
    KeyValue,
    KeyValueItem,
    KeyValueTitle,
    KeyValueText,
    BasicButton,
    ButtonList,
    ButtonListItem,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setActive(() => 'inventoryFinance003');
    });

    onUnmounted(() => {
      store.ui.header.setActive();
    });
  },
};
</script>

<template>
  <PageContents>
    <PageHead>
      <PageHeadRow>
        <PageTitle align="left">중도상환</PageTitle>
        <template v-slot:right>
          <StepProgress :total="4" :current="3" />
        </template>
      </PageHeadRow>
      <PageMainText align="left">
        중도 상환 조회 조건을 확인해주세요
      </PageMainText>
    </PageHead>

    <BasicBox>
      <KeyValue :wrap="true">
        <KeyValueItem>
          <KeyValueTitle>상환원금</KeyValueTitle>
          <KeyValueText>7,400,000 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>비용</KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>경과이자</KeyValueTitle>
          <KeyValueText>86,670 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>선수금 (환급금액)</KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>중도상환 수수료</KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>입금예정일</KeyValueTitle>
          <KeyValueText>2019.05.14</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>지연배상금</KeyValueTitle>
          <KeyValueText>0 원</KeyValueText>
        </KeyValueItem>

        <KeyValueItem>
          <KeyValueTitle>실납부액</KeyValueTitle>
          <KeyValueText>7,486,670 원</KeyValueText>
        </KeyValueItem>
      </KeyValue>
    </BasicBox>

    <div class="row-margin-block-small row-margin-bottom-none">
      // [공통 > 본인인증] 내용 노출
    </div>

    <ButtonList>
      <ButtonListItem>
        <BasicButton :line="true" theme="quaternary">다시 계산하기</BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton>중도상환신청</BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>
