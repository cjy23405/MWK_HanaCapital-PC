<script>
import { ref } from 'vue';

import PageContents from '@/components/ui/layout/PageContents.vue';
import BasicButton from '@/components/ui/button/BasicButton.vue';
import ButtonList from '@/components/ui/button/ButtonList.vue';
import ButtonListItem from '@/components/ui/button/ButtonListItem.vue';

import Agent_P02_l003 from '@/views/agent/Agent_P02_l003.vue';
import Agent_P02_l008 from '@/views/agent/Agent_P02_l008.vue';
import Agent_P00_l010 from '@/views/agent/Agent_P00_l010.vue';
import Agent_P00_l011 from '@/views/agent/Agent_P00_l011.vue';
import Agent_P02_l002 from '@/views/agent/Agent_P02_l002.vue';
import Agent_P02_l004 from '@/views/agent/Agent_P02_l004.vue';
import Agent_P02_l005 from '@/views/agent/Agent_P02_l005.vue';
import Agent_P02_l006 from '@/views/agent/Agent_P02_l006.vue';
import Agent_P02_l007 from '@/views/agent/Agent_P02_l007.vue';

export default {
  components: {
    PageContents,
    BasicButton,
    ButtonList,
    ButtonListItem,
    Agent_P02_l003,
    Agent_P02_l008,
    Agent_P00_l010,
    Agent_P00_l011,
    Agent_P02_l002,
    Agent_P02_l004,
    Agent_P02_l005,
    Agent_P02_l006,
    Agent_P02_l007,
  },
  setup() {
    const layer001 = ref(null);
    const layer002 = ref(null);
    const layer003 = ref(null);
    const layer004 = ref(null);
    const layer005 = ref(null);
    const layer006 = ref(null);
    const layer007 = ref(null);
    const layer008 = ref(null);
    const layer009 = ref(null);

    const layer001Open = (e = {}) => {
      layer001.value.layer.open(e.target);
    };
    const layer002Open = (e = {}) => {
      layer002.value.layer.open(e.target);
    };
    const layer003Open = (e = {}) => {
      layer003.value.layer.open(e.target);
    };
    const layer004Open = (e = {}) => {
      layer004.value.layer.open(e.target);
    };
    const layer005Open = (e = {}) => {
      layer005.value.layer.open(e.target);
    };
    const layer006Open = (e = {}) => {
      layer006.value.layer.open(e.target);
    };
    const layer007Open = (e = {}) => {
      layer007.value.layer.open(e.target);
    };
    const layer008Open = (e = {}) => {
      layer008.value.layer.open(e.target);
    };
    const layer009Open = (e = {}) => {
      layer009.value.layer.open(e.target);
    };

    return {
      layer001,
      layer002,
      layer003,
      layer004,
      layer005,
      layer006,
      layer007,
      layer008,
      layer009,
      layer001Open,
      layer002Open,
      layer003Open,
      layer004Open,
      layer005Open,
      layer006Open,
      layer007Open,
      layer008Open,
      layer009Open,
    };
  },
};
</script>

<template>
  <PageContents>
    <ButtonList
      :classNames="{
        wrap: 'row-margin-none',
      }"
      align="full"
    >
      <ButtonListItem>
        <BasicButton @click="layer001Open">
          상환스케쥴 팝업<br />Agent_P02_l003
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer002Open">
          민원세부정보 팝업<br />Agent_P02_l008
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer003Open">
          판매대리점조회 팝업<br />Agent_P00_l010
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer004Open">
          품목선택 팝업<br />Agent_P00_l011
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer005Open">
          상환스케쥴시뮬레이터 팝업<br />Agent_P02_l002
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer006Open">
          본인확인(본의명의휴대폰소지자) 팝업<br />Agent_P02_l004
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer007Open">
          하나캐피탈 전자 약정 URL 발송 팝업<br />Agent_P02_l005
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer008Open">
          판매점 제휴 협약을 위한 개인(신용)정보동의 URL 발송 팝업<br />Agent_P02_l006
        </BasicButton>
      </ButtonListItem>
      <ButtonListItem>
        <BasicButton @click="layer009Open">
          하나캐피탈 할부 상담 URL 발송<br />Agent_P02_l007
        </BasicButton>
      </ButtonListItem>
    </ButtonList>

    <Agent_P02_l003 ref="layer001" />
    <Agent_P02_l008 ref="layer002" />
    <Agent_P00_l010 ref="layer003" />
    <Agent_P00_l011 ref="layer004" />
    <Agent_P02_l002 ref="layer005" />
    <Agent_P02_l004 ref="layer006" />
    <Agent_P02_l005 ref="layer007" />
    <Agent_P02_l006 ref="layer008" />
    <Agent_P02_l007 ref="layer009" />
  </PageContents>
</template>
