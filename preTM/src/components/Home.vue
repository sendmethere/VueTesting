
<template>
  <v-main>
    <!-- 전체 컨테이너 -->
    <v-container class="#E5E5E5">
      <!-- 윈도우 -->
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-card flat>
              <v-window v-model="onboarding">
                <v-window-item v-for="n in length" :key="`card-${n}`">
                  <v-card rounded outlined color="grey" height="200">
                    <v-row class="fill-height" align="center" justify="center">
                      <h1 style="font-size: 5rem" class="white--text">
                        Slide {{ n }}
                      </h1>
                    </v-row>
                  </v-card>
                </v-window-item>
              </v-window>

              <v-card-actions class="justify-center">
                <v-item-group
                  v-model="onboarding"
                  class="text-center"
                  mandatory
                >
                  <v-item
                    v-for="n in length"
                    :key="`btn-${n}`"
                    v-slot="{ active, toggle }"
                  >
                    <v-btn icon :input-value="active" @click="toggle">
                      <v-icon>mdi-record</v-icon>
                    </v-btn>
                  </v-item>
                </v-item-group>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
      <!-- 두근두근 후기 -->
      <v-container>
        <v-row>
          <v-col cols="12">
            <v-card height="210" dense outlined rounded>
              <v-card-title class="pa-3">
                <v-icon color="secondary">mdi-heart-pulse</v-icon>
                &nbsp;&nbsp;두근두근 후기
              </v-card-title>
              <v-divider class="mx-5"></v-divider>
              <v-list>
                <v-list-item-group active-class="primary--text">
                  <template v-for="(post, index) in posts">
                    <v-list-item :key="index" dense>
                      <template>
                        <v-row no-gutters dense align="center">
                          <v-col cols="6" class="pa-0">
                            <v-list-item-content class="ml-3">
                              <v-list-item-title>{{
                                post.title
                              }}</v-list-item-title>
                            </v-list-item-content>
                          </v-col>

                          <v-col cols="3" class="pa-0 text-right">
                            <v-list-item-action>
                              <v-list-item-action-text>
                                <v-icon dense color="#A6A6A6">mdi-fire</v-icon
                                >32 &nbsp;
                                <v-icon dense color="#A6A6A6"
                                  >mdi-message-processing-outline</v-icon
                                >
                                35
                              </v-list-item-action-text>
                            </v-list-item-action>
                          </v-col>
                          <v-col cols="3" class="pa-0 text-right">
                            <v-list-item-action>
                              <v-list-item-action-text>
                                {{ post.owner }}
                                &nbsp;· &nbsp;{{ post.updated_at }}
                              </v-list-item-action-text>
                            </v-list-item-action>
                          </v-col>
                        </v-row>
                      </template>
                    </v-list-item>

                    <!-- <v-divider v-if="index < posts.length - 1" :key="index" class="mx-8"></v-divider> -->
                  </template>
                </v-list-item-group>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <!-- 작은 카드 -->
      <v-container>
        <v-row>
          <v-col  v-for="category in categories" :key="category.name" cols="6">
            <v-card height="210" dense outlined rounded>
              <v-card-title class="pa-3">
                <v-icon >{{category.icon}}</v-icon> &nbsp;&nbsp;{{category.name}}
              </v-card-title>
              <v-divider class="mx-5"></v-divider>
              <v-list>
                <v-list-item-group active-class="primary--text">
                  <template v-for="(post, index) in posts">
                    <v-list-item :key="index" dense>
                      <template>
                        <v-row no-gutters dense align="center">
                          <v-list-item-content class="ml-3">
                            <v-list-item-title>{{
                              post.title
                            }}</v-list-item-title>
                          </v-list-item-content>
                          <v-list-item-action>
                            <v-list-item-action-text>
                              <v-icon dense color="#A6A6A6">mdi-fire</v-icon>32
                              &nbsp;
                              <v-icon dense color="#A6A6A6"
                                >mdi-message-processing-outline</v-icon
                              >
                              35
                            </v-list-item-action-text>
                          </v-list-item-action>
                        </v-row>
                      </template>
                    </v-list-item>

                    <!-- <v-divider v-if="index < posts.length - 1" :key="index" class="mx-8"></v-divider> -->
                  </template>
                </v-list-item-group>
              </v-list>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-container>
  </v-main>
</template>

<script>
export default {
  data: () => ({
    categories: [
      { name: "헬스 · 다이어트", icon: "mdi-fire" },
      { name: "주식 · 투자", icon: "mdi-cash-plus" },
      { name: "썸 · 연애", icon: "mdi-puzzle-heart" },
      { name: "맛집 · 여행", icon: "mdi-coffee-outline" },
    ],
    posts: [
      {
        title: "개발보다 설레는 대상을 찾았어요...",
        content: "~~",
        owner: "행복한쌈코비빔밥dddddddd",
        updated_at: "2022.1.17",
      },
      {
        title: "드디어 사랑이 찾아오는가, 준봇의 두근두근 썰썰썰",
        content: "~~",
        owner: "둑흔준보",
        updated_at: "2022.1.17",
      },
      {
        title: "이제 나도 민간인! 기다려라 세상아.............................",
        content: "~~",
        owner: "자신있는라회택",
        updated_at: "2022.1.17",
      },
    ],
    length: 3,
    onboarding: 0,
  }),

  methods: {},
};
</script>

<style scoped></style>;
