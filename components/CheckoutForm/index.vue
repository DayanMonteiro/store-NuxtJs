<template>
  <div>
    <form class="form">
      <div class="containerForm">
        <div class="leftColumn">
          <div v-bind:class="{ 'fld-error': $v.form.name.$error }">
            <label>Nome*</label><br />
            <input
              type="text"
              class="inputLong"
              v-model.trim="form.name"
              @input="$v.form.name.$touch()"
            />
            <span class="msg-error" v-if="!$v.form.name.required">
              <small>Campo obrigatório</small>
            </span>
          </div>

          <div v-bind:class="{ 'fld-error': $v.form.email.$error }">
            <label>Email*</label><br />
            <input
              type="text"
              class="inputLong"
              v-model.trim="form.email"
              @input="$v.form.email.$touch()"
            />
            <span class="msg-error" v-if="!$v.form.email.required">
              <small>Campo obrigatório</small>
            </span>
          </div>

          <div v-bind:class="{ 'fld-error': $v.form.cpf.$error }">
            <label>CPF*</label><br />
            <input
              v-mask="'###.###.###-##'"
              type="text"
              class="inputLong"
              v-model.trim="form.cpf"
              @input="$v.form.cpf.$touch()"
            />
            <span class="msg-error" v-if="!$v.form.cpf.required">
              <small>Campo obrigatório</small>
            </span>
          </div>

          <div class="towInputs">
            <div v-bind:class="{ 'fld-error': $v.form.birthDate.$error }">
              <label>Data de Nascimento*</label><br />
              <input
                v-mask="'##/##/####'"
                type="text"
                class="inputMedium"
                v-model.trim="form.birthDate"
                @input="$v.form.birthDate.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.birthDate.required">
                <small>Campo obrigatório</small>
              </span>
            </div>

            <div v-bind:class="{ 'fld-error': $v.form.telephone.$error }">
              <label>Telefone*</label><br />
              <input
                v-mask="['(##) #####-####', '(##) ####-####']"
                type="text"
                class="inputMedium"
                v-model.trim="form.telephone"
                @input="$v.form.telephone.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.telephone.required">
                <small>Campo obrigatório</small>
              </span>
            </div>
          </div>
        </div>

        <div class="rightColumn">
          <div v-bind:class="{ 'fld-error': $v.form.cep.$error }">
            <label>CEP*</label><br />
            <input
              v-mask="'##.###-###'"
              type="text"
              class="inputLong"
              v-model.trim="form.cep"
              @input="$v.form.cep.$touch()"
            />
            <span class="msg-error" v-if="!$v.form.cep.required">
              <small>Campo obrigatório</small>
            </span>
          </div>

          <div class="towInputs">
            <div v-bind:class="{ 'fld-error': $v.form.address.$error }">
              <label>Endereço*</label><br />
              <input
                type="text"
                class="inputXMedium"
                v-model.trim="form.address"
                @input="$v.form.address.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.address.required">
                <small>Campo obrigatório</small>
              </span>
            </div>

            <div v-bind:class="{ 'fld-error': $v.form.number.$error }">
              <label>Número*</label><br />
              <input
                type="text"
                class="inputSmall"
                v-model.trim="form.number"
                @input="$v.form.number.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.number.required">
                <small>Campo obrigatório</small>
              </span>
            </div>
          </div>

          <div class="towInputs">
            <div>
              <label>Complemento</label><br />
              <input
                type="text"
                class="inputMedium"
                v-model.trim="form.complement"
                @input="$vcomplement.$touch()"
              />
            </div>

            <div v-bind:class="{ 'fld-error': $v.form.district.$error }">
              <label>Bairro*</label><br />
              <input
                type="text"
                class="inputMedium"
                v-model.trim="form.district"
                @input="$v.form.district.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.district.required">
                <small>Campo obrigatório</small>
              </span>
            </div>
          </div>

          <div class="towInputs">
            <div v-bind:class="{ 'fld-error': $v.form.city.$error }">
              <label>Cidade*</label><br />
              <input
                type="text"
                class="inputXMedium"
                v-model.trim="form.city"
                @input="$v.form.city.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.city.required">
                <small>Campo obrigatório</small>
              </span>
            </div>

            <div v-bind:class="{ 'fld-error': $v.form.state.$error }">
              <label>Estado*</label><br />
              <input
                type="text"
                class="inputSmall"
                v-model.trim="form.state"
                @input="$v.form.state.$touch()"
              />
              <span class="msg-error" v-if="!$v.form.state.required">
                <small>Campo obrigatório</small>
              </span>
            </div>
          </div>
        </div>
      </div>

      <div class="containerButton">
        <button
          type="submit"
          @click.prevent="submitForm"
          :disabled="$v.form.$invalid"
        >
          Concluir compra
        </button>
      </div>
    </form>
  </div>
</template>

<script type="text/javascript">
import axios from "axios";
import { required } from "vuelidate/lib/validators";
import { mask } from "vue-the-mask";

export default {
  name: "CheckoutForm",

  directives: { mask },

  data() {
    return {
      form: {
        name: "",
        email: "",
        cpf: "",
        birthDate: "",
        telephone: "",
        cep: "",
        address: "",
        number: "",
        complement: "",
        district: "",
        city: "",
        state: "",
      },
    };
  },

  validations: {
    form: {
      name: {
        required,
      },
      email: {
        required,
      },
      cpf: {
        required,
      },
      birthDate: {
        required,
      },
      telephone: {
        required,
      },
      cep: {
        required,
      },
      address: {
        required,
      },
      number: {
        required,
      },
      district: {
        required,
      },
      city: {
        required,
      },
      state: {
        required,
      },
    },
  },

  methods: {
    submitForm() {
      let contactFormData = new FormData();
      contactFormData.set("name", this.form.name);
      contactFormData.set("email", this.form.email);
      contactFormData.set("cpf", this.form.cpf);
      contactFormData.set("birthDate", this.form.birthDate);
      contactFormData.set("telephone", this.form.telephone);
      contactFormData.set("cep", this.form.cep);
      contactFormData.set("address", this.form.address);
      contactFormData.set("number", this.form.number);
      contactFormData.set("district", this.form.district);
      contactFormData.set("city", this.form.city);
      contactFormData.set("state", this.form.state);
      console.log("submitting data...");
      axios({
        method: "post",
        url: "https://630fc9bf498924524a95b105.mockapi.io/users",
        data: contactFormData,
      })
        .then(function (response) {
          alert("Cadastrado com sucesso!");

          console.log(response);
        })
        .catch(function (response) {
          // Handle error.

          console.log(response);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
.form {
  margin-top: 8rem;
  margin-bottom: 8rem;
}

.containerForm {
  display: flex;
  flex-direction: row;
  width: 62rem;
  justify-content: space-between;
}

.leftColumn {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}

.rightColumn {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.inputLong {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  border: none;
  height: 3rem;
  width: 30rem;
  border: 1px solid gray;
}

.inputXMedium {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  border: none;
  height: 3rem;
  width: 19rem;
  border: 1px solid gray;
}
.inputMedium {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  border: none;
  height: 3rem;
  width: 14rem;
  border: 1px solid gray;
}

.inputSmall {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  border: none;
  height: 3rem;
  width: 9rem;
  border: 1px solid gray;
}

.towInputs {
  display: flex;
  flex-direction: row;
  width: 100%;
  justify-content: space-between;
}

label {
  color: #909090;
}
.fld-error .msg-error {
  display: block;
}
.msg-error {
  display: none;
}

.containerButton {
  display: flex;
  justify-content: flex-end;
}

button {
  background-color: #8a2be2;
  color: #fff;
  width: 20rem;
  height: 3rem;
  font-weight: bold;
  border-radius: 0.2rem;
  margin-top: 0.1rem;
}
</style>
