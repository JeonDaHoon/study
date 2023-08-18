<template>
  <fieldset>
    <legend>Vue 2 Class Component</legend>
    <form @submit.prevent="loginUseRef">
      <label for="id">
        ID
        <input ref="idRef" id="id" name="id" type="text" v-model="id" />
      </label>
      <label for="pw">
        PW
        <input ref="pwRef" id="pw" name="pw" type="password" v-model="password" />
      </label>
      <button type="submit">
        LOGIN
      </button>
    </form>
  </fieldset>

  <hr />

  <fieldset>
    <legend>Vue 2 Class Component</legend>
    <form @submit.prevent="loginUseReactive">
      <label for="id">
        ID
        <input ref="idRef" id="id2" name="id" type="text" v-model="loginData.id" />
      </label>
      <label for="pw">
        PW
        <input ref="pwRef" id="pw2" name="pw" type="password" v-model="loginData.password" />
      </label>
      <button type="submit">
        LOGIN
      </button>
    </form>
  </fieldset>
</template>

<script lang="ts" setup>
import {reactive, Ref, ref} from "vue";

interface Login {
  id: string;
  password: string;
}
// ref 사용
const id = ref<string>('');
const password = ref<string>('');
// reactive 사용
const loginData = reactive<Login>({ id:'', password: '' });

const idRef: Ref<HTMLInputElement | null> = ref(null);
const pwRef: Ref<HTMLInputElement | null> = ref(null);

const loginUseRef = async (): Promise<void> => {
  const check = validationCheck();
  if (check)
    alert(`입력된 ID : ${id.value}, PW : ${password.value} - ref 를 활용`);
}

const loginUseReactive = async (): Promise<void> => {

}

const validationCheck = (): boolean => {
  const idCheck = id.value.length > 0;
  const passwordCheck = password.value.length > 0;

  if (!idCheck) idRef.value!.focus();
  else if (!passwordCheck) pwRef.value?.focus();

  return idCheck && passwordCheck;
}

</script>

<style scoped lang="scss">
#id:focus {
  border-color: #42b983;
}

#pw:focus {
  border-color: #42b983;
}
</style>