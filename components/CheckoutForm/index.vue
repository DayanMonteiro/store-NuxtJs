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
  name: "CheckoutFormMobile",

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

@font-face {
    font-family: 'SoucerSansPro-Regular';
    src: url('../../resources/fonts/SourceSansPro-Regular.ttf') format('truetype');
  }
.form {
  margin-top: 8rem;
  margin-bottom: 8rem;
}

.containerForm {
  display: flex;
  justify-content: space-between;
  font-family: 'SoucerSansPro-Regular';

  @media only screen and (min-width: 360px) {
    width: 20rem ;
    flex-direction: column;
  }

  @media only screen and (min-width: 640px) {
    width: 30rem ;
  }

  @media only screen and (min-width: 910px) {
    width: 38rem ;
  }

  @media only screen and (min-width: 1080px) {
    flex-direction: row;
    justify-content: space-between;
    width: 42rem;
  }

  @media only screen and (min-width: 1360px) {
    width: 50rem;
  }

  @media only screen and (min-width: 1640px) {
    width: 58rem;
  }

  @media only screen and (min-width: 1780px) {
    width: 65rem;
  } 

}

.leftColumn {
  @media only screen and (min-width: 1080px) {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  }
}

.rightColumn {

  @media only screen and (min-width: 1080px) {
    display: flex;
    flex-direction: column; 
  }
}
.inputLong {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  height: 2.5rem;
  border-radius: 0.2rem;
  border: 1px solid gray;

  @media only screen and (min-width: 360px) {
    width: 20rem;
  }

  @media only screen and (min-width: 640px) {
    width: 30rem;
  }

  @media only screen and (min-width: 910px) {
   width: 38rem;
  }

  @media only screen and (min-width: 1080px) {
    width: 20rem;
  }

  @media only screen and (min-width: 1360px) {
    width: 24rem;
  }

  @media only screen and (min-width: 1640px) {
    width: 28rem;
  }

  @media only screen and (min-width: 1780px) {
    width: 31rem;
  }

}

.inputXMedium {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  height: 2.5rem;
  border-radius: 0.2rem;
  border: 1px solid gray;

  @media only screen and (min-width: 360px) {
    width: 11rem;
  }

  @media only screen and (min-width: 640px) {
    width: 17rem;
  }

  @media only screen and (min-width: 910px) {
    width: 25rem;
  }

  @media only screen and (min-width: 1080px) {
    width: 11rem;
  }

  @media only screen and (min-width: 1360px) {
    width: 15rem;
  }

  @media only screen and (min-width: 1640px) {
    width: 19rem;
  }

  @media only screen and (min-width: 1780px) {
    width: 19.7rem;
  }

}
.inputMedium {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  height: 2.5rem;
  border-radius: 0.2rem;
  border: 1px solid gray;

  @media only screen and (min-width: 360px) {
   // background-color: yellow;
    width: 9rem;
  }


  @media only screen and (min-width: 640px) {
    width: 14rem;
  }

  @media only screen and (min-width: 910px) {
    width: 18rem;
  }

  @media only screen and (min-width: 1080px) {
    width: 9rem;
  }

  @media only screen and (min-width: 1360px) {
    width: 11rem;
  }

  @media only screen and (min-width: 1640px) {
    width: 13rem;
  }

  @media only screen and (min-width: 1780px) {
   width: 14.7rem;
  }

}

.inputSmall {
  float: left;
  margin-top: 0.3rem;
  margin-bottom: 1rem;
  padding-left: 1rem;
  font-style: italic;
  font-size: 18px;
  height: 2.5rem;
  border-radius: 0.2rem;
  border: 1px solid gray;

  @media only screen and (min-width: 360px) {
    width: 7rem;
  }

  @media only screen and (min-width: 640px) {
    width: 11rem;
  }

  @media only screen and (min-width: 1080px) {
    width: 7rem;
  }

  @media only screen and (min-width: 1360px) {
    width: 10rem;
  }

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
  border-radius: 0.2rem;
  margin-top: 0.1rem;
  font-family: 'SoucerSansPro-Regular';
}
</style>
