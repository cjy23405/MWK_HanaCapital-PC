<script>
// LM_P04_p001
import { onMounted, onUnmounted } from 'vue';

import { useUiHeaderStore } from '@/stores/ui/header';

import PageContents from '@/components/ui/layout/PageContents.vue';
import PageHead from '@/components/ui/text/PageHead.vue';
import PageTitle from '@/components/ui/text/PageTitle.vue';
import FormList from '@/components/ui/form/FormList.vue';
import FormListItem from '@/components/ui/form/FormListItem.vue';
import InputBlock from '@/components/ui/form/InputBlock.vue';
import InputBlockCell from '@/components/ui/form/InputBlockCell.vue';
import BasicSelect from '@/components/ui/form/BasicSelect.vue';

export default {
  components: {
    PageContents,
    PageHead,
    PageTitle,
    FormList,
    FormListItem,
    InputBlock,
    InputBlockCell,
    BasicSelect,
  },
  setup() {
    const store = {
      ui: {
        header: useUiHeaderStore(),
      },
    };

    onMounted(() => {
      store.ui.header.setActive(() => 'lmBlog003');
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
      <PageTitle>접속통계</PageTitle>
    </PageHead>

    <FormList>
      <FormListItem
        titleText="통계년도"
        target="#LM_P04_p001_year"
        :selectOnly="true"
      >
        <InputBlock>
          <InputBlockCell :flexible="true">
            <BasicSelect
              :options="[
                {
                  value: '1',
                  label: '2022',
                },
                {
                  value: '2',
                  label: '2021',
                },
                {
                  value: '3',
                  label: '2020',
                },
                {
                  value: '4',
                  label: '2019',
                },
                {
                  value: '5',
                  label: '2018',
                },
                {
                  value: '6',
                  label: '2017',
                },
              ]"
              title="통계년도"
              inputId="LM_P04_p001_year"
              defaultValue="1"
            />
          </InputBlockCell>
        </InputBlock>
      </FormListItem>
    </FormList>

    <!-- table -->
    <div :class="[$style['basic-table'], 'row-margin-block-small']">
      <table>
        <colgroup>
          <col style="width: 200px" />
          <col />
        </colgroup>
        <thead>
          <tr>
            <th>월</th>
            <th>방문자</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>1</td>
            <td>1</td>
          </tr>
          <tr>
            <td>2</td>
            <td>2</td>
          </tr>
          <tr>
            <td>3</td>
            <td>0</td>
          </tr>
          <tr>
            <td>4</td>
            <td>58</td>
          </tr>
          <tr>
            <td>5</td>
            <td>0</td>
          </tr>
          <tr>
            <td>6</td>
            <td>0</td>
          </tr>
          <tr>
            <td>7</td>
            <td>0</td>
          </tr>
          <tr>
            <td>8</td>
            <td>0</td>
          </tr>
          <tr>
            <td>9</td>
            <td>0</td>
          </tr>
          <tr>
            <td>10</td>
            <td>0</td>
          </tr>
          <tr>
            <td>11</td>
            <td>0</td>
          </tr>
          <tr>
            <td>12</td>
            <td>0</td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td>합계</td>
            <td>61</td>
          </tr>
        </tfoot>
      </table>
    </div>
    <!-- // table -->
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/lmBlog/LM_P04_p001.scss';
</style>
