<template>
  <fieldset>
    <legend>Vue 2 Class Component</legend>
    <form @submit.prevent="login">
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
</template>

<script lang="ts">
import {Ref, Vue} from "vue-property-decorator";
import Component from "vue-class-component";

@Component({})
export default class SigninForm extends Vue {
  @Ref() idRef: HTMLInputElement | undefined;
  @Ref() pwRef: HTMLInputElement | undefined;

  id = '';
  password = '';

  async login(): Promise<void> {
    const check = this.validationCheck();
    if (check)
      alert(`입력된 ID : ${this.id}, PW : ${this.password}`);
  }

  validationCheck(): boolean {
    const idCheck = this.id.length > 0;
    const passwordCheck = this.password.length > 0;

    if (!idCheck) this.idRef?.focus();
    else if (!passwordCheck) this.pwRef?.focus();

    return idCheck && passwordCheck;
  }
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