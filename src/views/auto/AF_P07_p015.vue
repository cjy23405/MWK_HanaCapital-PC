<script>
// AF_P07_p015
import { onMounted, onUnmounted } from 'vue';

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
import BasicTooltip from '@/components/ui/tooltip/BasicTooltip.vue';

import IconImgColor from '@/assets/images/icon/img-color.svg?component';
import IconImg from '@/assets/images/icon/img.svg?component';
import IconTooltip from '@/assets/images/icon/tooltip.svg?component';

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
    BasicTooltip,
    IconImgColor,
    IconImg,
    IconTooltip,
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
            text: '오토승계',
            to: '/',
          },
        ]"
      />
    </template>

    <PageHead>
      <PageHeadRow>
        <PageTitle align="left">오토승계</PageTitle>
        <template v-slot:right>
          <StepProgress :total="3" :current="2" />
        </template>
      </PageHeadRow>
      <PageMainText align="left">서류를 등록해 주세요</PageMainText>
    </PageHead>

    <div>
      <ul class="reset-list">
        <li class="row-margin-contents">
          <div :class="$style['upload-button']">
            <input
              type="file"
              id="AF_P07_p015_upload001"
              :class="$style['upload-button__input']"
            />
            <div :class="$style['upload-button__block']">
              <span :class="$style['upload-button__img']">
                <IconImg />
              </span>
              <label
                for="AF_P07_p015_upload001"
                :class="$style['upload-button__label']"
              >
                운전면허증(운전경력증명서)
              </label>
            </div>
          </div>

          <!-- Case : 비활성화 상태일 때 -->
          <div :class="$style['upload-button']">
            <input
              type="file"
              id="AF_P07_p015_upload001Disabled"
              :class="$style['upload-button__input']"
              :disabled="true"
            />
            <div :class="$style['upload-button__block']">
              <span :class="$style['upload-button__img']">
                <IconImg />
              </span>
              <label
                for="AF_P07_p015_upload001Disabled"
                :class="$style['upload-button__label']"
              >
                운전면허증(운전경력증명서)
              </label>
            </div>
          </div>
          <!-- //Case : 비활성화 상태일 때 -->

          <!-- Case : 파일 첨부 후 -->
          <div
            :class="[
              $style['upload-file'],
              $style['upload-file--inside'],
              $style['upload-file--child'],
            ]"
          >
            <ul :class="$style['upload-file__list']">
              <li :class="$style['upload-file__item']">
                <div :class="$style['upload-file__icon']">
                  <IconImgColor />
                </div>
                <div :class="$style['upload-file__content']">
                  <div :class="$style['upload-file__name']">
                    첨부된파일명입력.pdf
                  </div>
                </div>
                <div :class="$style['upload-file__button']">
                  <BasicButton :line="true" theme="quaternary" size="small">
                    삭제
                  </BasicButton>
                </div>
              </li>
            </ul>
          </div>
          <!-- //Case : 파일 첨부 후 -->
        </li>

        <li class="row-margin-contents">
          <div :class="$style['upload-button']">
            <input
              type="file"
              id="AF_P07_p015_upload002"
              :class="$style['upload-button__input']"
            />
            <div :class="$style['upload-button__block']">
              <span :class="$style['upload-button__img']">
                <IconImg />
              </span>
              <label
                for="AF_P07_p015_upload002"
                :class="$style['upload-button__label']"
              >
                건강보험자격득실확인서
              </label>
              <div :class="$style['upload-button__tooltip']">
                <BasicTooltip>
                  <IconTooltip class="display-block" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        건강보험득실확인서
                      </h3>
                      <ul
                        :class="[
                          $style['basic-list'],
                          $style['basic-list--small-margin'],
                        ]"
                      >
                        <li
                          :class="[$style['basic-list__item'], 'color-white']"
                        >
                          <div :class="$style['basic-list__symbol']"></div>
                          <div :class="$style['basic-list__content']">
                            재직확인을 위한 서류: 건강보험자격득실확인서,
                            재직증명서 등
                          </div>
                        </li>
                      </ul>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </div>

          <!-- Case : 파일 첨부 후 -->
          <div
            :class="[
              $style['upload-file'],
              $style['upload-file--inside'],
              $style['upload-file--child'],
            ]"
          >
            <ul :class="$style['upload-file__list']">
              <li v-for="i in 4" :key="i" :class="$style['upload-file__item']">
                <div :class="$style['upload-file__icon']">
                  <IconImgColor />
                </div>
                <div :class="$style['upload-file__content']">
                  <div :class="$style['upload-file__name']">
                    첨부된파일명입력.pdf
                  </div>
                </div>
                <div :class="$style['upload-file__button']">
                  <BasicButton :line="true" theme="quaternary" size="small">
                    삭제
                  </BasicButton>
                </div>
              </li>
            </ul>
          </div>
          <!-- //Case : 파일 첨부 후 -->
        </li>

        <li class="row-margin-contents">
          <div :class="$style['upload-button']">
            <input
              type="file"
              id="AF_P07_p015_upload003"
              :class="$style['upload-button__input']"
            />
            <div :class="$style['upload-button__block']">
              <span :class="$style['upload-button__img']">
                <IconImg />
              </span>
              <label
                for="AF_P07_p015_upload003"
                :class="$style['upload-button__label']"
              >
                소득금액증명원
              </label>
              <div :class="$style['upload-button__tooltip']">
                <BasicTooltip>
                  <IconTooltip class="display-block" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        소득금액증명원
                      </h3>
                      <ul
                        :class="[
                          $style['basic-list'],
                          $style['basic-list--small-margin'],
                        ]"
                      >
                        <li
                          :class="[$style['basic-list__item'], 'color-white']"
                        >
                          <div :class="$style['basic-list__symbol']"></div>
                          <div :class="$style['basic-list__content']">
                            소득확인을 위한 서류: 소득금액증명원,
                            원천징수영수증, 건강보험료납부확인서 등
                          </div>
                        </li>
                      </ul>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </div>

          <!-- Case : 파일 첨부 후 -->
          <div
            :class="[
              $style['upload-file'],
              $style['upload-file--inside'],
              $style['upload-file--child'],
            ]"
          >
            <ul :class="$style['upload-file__list']">
              <li v-for="i in 4" :key="i" :class="$style['upload-file__item']">
                <div :class="$style['upload-file__icon']">
                  <IconImgColor />
                </div>
                <div :class="$style['upload-file__content']">
                  <div :class="$style['upload-file__name']">
                    첨부된파일명입력.pdf
                  </div>
                </div>
                <div :class="$style['upload-file__button']">
                  <BasicButton :line="true" theme="quaternary" size="small">
                    삭제
                  </BasicButton>
                </div>
              </li>
            </ul>
          </div>
          <!-- //Case : 파일 첨부 후 -->
        </li>

        <li class="row-margin-contents">
          <div :class="$style['upload-button']">
            <input
              type="file"
              id="AF_P07_p015_upload004"
              :class="$style['upload-button__input']"
            />
            <div :class="$style['upload-button__block']">
              <span :class="$style['upload-button__img']">
                <IconImg />
              </span>
              <label
                for="AF_P07_p015_upload004"
                :class="$style['upload-button__label']"
              >
                기타서류
              </label>
              <div :class="$style['upload-button__tooltip']">
                <BasicTooltip>
                  <IconTooltip class="display-block" />
                  <span class="for-a11y">(도움말)</span>

                  <template v-slot:contents>
                    <section :class="$style['tooltip-section']">
                      <h3 :class="$style['tooltip-section__title']">
                        기타서류
                      </h3>
                      <ul
                        :class="[
                          $style['basic-list'],
                          $style['basic-list--small-margin'],
                        ]"
                      >
                        <li
                          :class="[$style['basic-list__item'], 'color-white']"
                        >
                          <div :class="$style['basic-list__symbol']"></div>
                          <div :class="$style['basic-list__content']">
                            심사를 위한 추가서류: 재산세납입증명원,
                            전문직증빙서류 등
                          </div>
                        </li>
                      </ul>
                    </section>
                  </template>
                </BasicTooltip>
              </div>
            </div>
          </div>

          <!-- Case : 파일 첨부 후 -->
          <div
            :class="[
              $style['upload-file'],
              $style['upload-file--inside'],
              $style['upload-file--child'],
            ]"
          >
            <ul :class="$style['upload-file__list']">
              <li v-for="i in 4" :key="i" :class="$style['upload-file__item']">
                <div :class="$style['upload-file__icon']">
                  <IconImgColor />
                </div>
                <div :class="$style['upload-file__content']">
                  <div :class="$style['upload-file__name']">
                    첨부된파일명입력.pdf
                  </div>
                </div>
                <div :class="$style['upload-file__button']">
                  <BasicButton :line="true" theme="quaternary" size="small">
                    삭제
                  </BasicButton>
                </div>
              </li>
            </ul>
          </div>
          <!-- //Case : 파일 첨부 후 -->
        </li>
      </ul>

      <ul
        :class="[
          $style['basic-list'],
          $style['basic-list--regular-margin'],
          'row-margin-contents',
        ]"
      >
        <li :class="$style['basic-list__item']">
          <div :class="$style['basic-list__symbol']"></div>
          <div :class="[$style['basic-list__content'], 'font-weight-light']">
            서류등록파일은 이미지 파일만 가능합니다. (jpg, jpeg, png, gif 파일)
          </div>
        </li>
        <li :class="$style['basic-list__item']">
          <div :class="$style['basic-list__symbol']"></div>
          <div :class="[$style['basic-list__content'], 'font-weight-light']">
            서류등록파일은 1회 접속 시 최대 5개까지 등록 가능하며 추가적인
            서류등록을 원하실 경우 서류등록 메뉴에 재접속하여 추가등록해 주세요.
          </div>
        </li>
        <li :class="$style['basic-list__item']">
          <div :class="$style['basic-list__symbol']"></div>
          <div :class="[$style['basic-list__content'], 'font-weight-light']">
            고객님께서 제출하신 서류는 본 금융거래 이외의 다른 목적으로 사용되지
            않습니다.
          </div>
        </li>
        <li :class="$style['basic-list__item']">
          <div :class="$style['basic-list__symbol']"></div>
          <div :class="[$style['basic-list__content'], 'font-weight-light']">
            외국인 : 국내거소사실증명원, 국내거소신고증(앞/뒷면)
          </div>
        </li>
        <li :class="$style['basic-list__item']">
          <div :class="$style['basic-list__symbol']"></div>
          <div :class="[$style['basic-list__content'], 'font-weight-light']">
            렌터카 임직원 상품 승계 시 임직원 증빙자료를 꼭 등록해주세요.
          </div>
        </li>
      </ul>
    </div>

    <ButtonList>
      <ButtonListItem>
        <BasicButton>다음</BasicButton>
      </ButtonListItem>
    </ButtonList>
  </PageContents>
</template>

<style lang="scss" module>
@import '@/assets/scss/views/auto/AF_P07_p015.scss';
</style>
