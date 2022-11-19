<template>
  <div >
	<form class="form">
	<!-- <form v-on:submit.prevent="submitForm">  -->

    <div class="containerForm">
    <!-- CRIAR UMA DIV COM CLASS COLUMNLEFT -->
    <div class="leftColumn"> 

  
    <!-- CAMPO NOME -->
		<div v-bind:class="{ 'fld-error': $v.form.name.$error }">
			<label>Nome*</label><br>
			<input type="text" class="inputLong" v-model.trim="form.name" @input="$v.form.name.$touch()">


			<span class="msg-error" v-if="!$v.form.name.required">
				<small>Campo obrigatório</small>
			</span>
			<!-- <span class="msg-error" v-if="!$v.form.name.minLength">
				<small>Name must have at least {{ $v.form.name.$params.minLength.min }} letters.</small>
			</span> -->
		</div>

        <!-- CAMPO EMAIL -->
    <div v-bind:class="{ 'fld-error': $v.form.email.$error }">
			<label>Email*</label><br>
			<input type="text" class="inputLong" v-model.trim="form.email" @input="$v.form.email.$touch()">


			<span class="msg-error" v-if="!$v.form.email.required">
				<small>Campo obrigatório</small>
			</span>

			<!-- <span class="msg-error" v-if="!$v.form.email.minLength">
				<small>Name must have at least {{ $v.form.email.$params.minLength.min }} letters.</small>
			</span> -->
		</div>

           <!-- CAMPO CPF -->
    <div v-bind:class="{ 'fld-error': $v.form.cpf.$error }">
			<label>CPF*</label><br>
			<input type="text" class="inputLong" v-model.trim="form.cpf" @input="$v.form.cpf.$touch()">


			<span class="msg-error" v-if="!$v.form.cpf.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

      <!-- XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX -->
      <!-- -->
    <div class="towInputs" >
       <!-- CAMPO DATA DE NASCIMENTO -->
      <div v-bind:class="{ 'fld-error': $v.form.birthDate.$error }">
			<label>Data de Nascimento*</label><br>
			<input type="text" class="inputMedium" v-model.trim="form.birthDate" @input="$v.form.birthDate.$touch()">


			<span class="msg-error" v-if="!$v.form.birthDate.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

     <!-- CAMPO TELEFONE -->
    <div v-bind:class="{ 'fld-error': $v.form.telephone.$error }">
			<label>Telefone*</label><br>
			<input type="text" class="inputMedium" v-model.trim="form.telephone" @input="$v.form.telephone.$touch()">


			<span class="msg-error" v-if="!$v.form.telephone.required">
				<small>Campo obrigatório</small>
			</span>
		</div>
  </div>
    </div>



		<!-- <div v-bind:class="{ 'fld-error': $v.form.job.$error }">
			<label>Job</label><br>
			<input type="text" v-model="form.job" @input="$v.form.job.$touch()">

			<span class="msg-error" v-if="!$v.form.job.required">
				<small>Field is required</small>
			</span>
		</div> -->

   <!-- CRIAR UMA DIV COM CLASS COLUMNRigth -->
   <div class="rightColumn" >
                 <!-- CAMPO CEP -->
    <div v-bind:class="{ 'fld-error': $v.form.cep.$error }">
			<label>CEP*</label><br>
			<input type="text" class="inputLong" v-model.trim="form.cep" @input="$v.form.cep.$touch()">


			<span class="msg-error" v-if="!$v.form.cep.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

    <div class="towInputs" >
      <!-- CAMPO ENDEREÇO -->
      <div v-bind:class="{ 'fld-error': $v.form.address.$error }">
			<label>Endereço*</label><br>
			<input type="text" class="inputXMedium" v-model.trim="form.address" @input="$v.form.address.$touch()">


			<span class="msg-error" v-if="!$v.form.address.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

     <!-- CAMPO RUA -->
    <div v-bind:class="{ 'fld-error': $v.form.number.$error }">
			<label>Número*</label><br>
			<input type="text" class="inputSmall" v-model.trim="form.number" @input="$v.form.number.$touch()">


			<span class="msg-error" v-if="!$v.form.number.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

    </div>
    
    <div class="towInputs" >
      <!-- CAMPO ENDEREÇO -->
      <div >
			<label>Complemento</label><br>
			<input type="text" class="inputMedium" v-model.trim="form.complement" @input="$vcomplement.$touch()">
		</div>

     <!-- CAMPO RUA -->
    <div v-bind:class="{ 'fld-error': $v.form.district.$error }">
			<label>Bairro*</label><br>
			<input type="text" class="inputMedium" v-model.trim="form.district" @input="$v.form.district.$touch()">


			<span class="msg-error" v-if="!$v.form.district.required">
				<small>Campo obrigatório</small>
			</span>
		</div>
    </div>


    <div class="towInputs" >
      <!-- CAMPO ENDEREÇO -->
      <div v-bind:class="{ 'fld-error': $v.form.city.$error }">
			<label>Cidade*</label><br>
			<input type="text" class="inputXMedium" v-model.trim="form.city" @input="$v.form.city.$touch()">


			<span class="msg-error" v-if="!$v.form.city.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

     <!-- CAMPO RUA -->
    <div v-bind:class="{ 'fld-error': $v.form.state.$error }">
			<label>Estado*</label><br>
			<input type="text" class="inputSmall" v-model.trim="form.state" @input="$v.form.state.$touch()">


			<span class="msg-error" v-if="!$v.form.state.required">
				<small>Campo obrigatório</small>
			</span>
		</div>

    </div>
   </div>



  </div>
		<div class="containerButton">
			<button type="submit" @click.prevent="submitForm" :disabled="$v.form.$invalid">Concluir compra</button>
    </div>
	</form>
</div>
</template>

<script type="text/javascript">
	import axios from 'axios'
	import { required, minLength } from 'vuelidate/lib/validators'
	export default {
    name: "CheckoutForm",

		data() {
			return {
				form: {
					name: '',
          email: '',
          cpf: '',
          birthDate: '',
          telephone: '',
          cep: '',
          address: '',
          number: '',
					complement: '',
          district: '',
          city: '',
          state: '',
				}
			}
			
		},
		validations: {
			form: {
				name: {
					required,
					//  minLength: minLength( 4 )
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
        }
			}
		},
		methods: {
			submitForm() {
				let contactFormData = new FormData();
				contactFormData.set( 'name', this.form.name );
        contactFormData.set( 'email', this.form.email );
        contactFormData.set( 'cpf', this.form.cpf);
        contactFormData.set( 'birthDate', this.form.birthDate);
        contactFormData.set( 'telephone', this.form.telephone);
        contactFormData.set( 'cep', this.form.cep);
        contactFormData.set( 'address', this.form.address);
        contactFormData.set( 'number', this.form.number);
        contactFormData.set( 'district', this.form.district);
        contactFormData.set( 'city', this.form.city);
        contactFormData.set( 'state', this.form.state);


				// contactFormData.set( 'job', this.form.job );
				console.log( 'submitting data...' );
				axios( {
					method: 'post',
					url: 'https://reqres.in/api/users',
					data: contactFormData
				} ).then( function ( response ) {
					// Handle success.
					
					console.log( response );
				} ).catch( function ( response ) {
					// Handle error.
					
					console.log( response );
				} );
			}
		}
	}
</script>

<style lang="scss"scoped >

  .form{
 //   background-color: red;
    margin-top: 8rem;
    margin-bottom: 8rem;
   // width: 57%;
  // height: 100rem;
  }

  .containerForm{
   // background-color: pink;
    display: flex;
    flex-direction: row;
    width: 62rem;
    // align-items: flex-start;
    justify-content: space-between; 
  }


  .leftColumn{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
  //  background-color: red;
  }

  .rightColumn{
    display: flex;
    flex-direction: column;
    align-items: flex-start;
   // background-color: blue;
  }
  .inputLong{
    float:left;
  //  background-color:transparent;
  //  background-color: red;
    margin-top: 0.3rem;
    margin-bottom: 1rem;
    padding-left: 1rem;
    font-style:italic;
    font-size:18px;
    border:none;
    height: 3rem;
    width: 30rem; 
    border: 1px solid gray;
    /* border-bottom-left-radius: 5px;
    border-top-left-radius: 5px; */
  }

  .inputXMedium{
    float:left;
  //  background-color:transparent;
  //  background-color: red;
    margin-top: 0.3rem;
    margin-bottom: 1rem;
    padding-left: 1rem;
    font-style:italic;
    font-size:18px;
    border:none;
    height: 3rem;
    width: 19rem; 
    border: 1px solid gray;
    /* border-bottom-left-radius: 5px;
    border-top-left-radius: 5px; */
  }
  .inputMedium{
    float:left;
  //  background-color:transparent;
  //  background-color: red;
    margin-top: 0.3rem;
    margin-bottom: 1rem;
    padding-left: 1rem;
    font-style:italic;
    font-size:18px;
    border:none;
    height: 3rem;
    width: 14rem; 
    border: 1px solid gray;
    /* border-bottom-left-radius: 5px;
    border-top-left-radius: 5px; */
  }

  .inputSmall{
    float:left;
  //  background-color:transparent;
  //  background-color: red;
    margin-top: 0.3rem;
    margin-bottom: 1rem;
    padding-left: 1rem;
    font-style:italic;
    font-size:18px;
    border:none;
    height: 3rem;
    width: 9rem; 
    border: 1px solid gray;
    /* border-bottom-left-radius: 5px;
    border-top-left-radius: 5px; */
  }

  .towInputs{
   // margin-top: 4rem; 
    display: flex;
    flex-direction: row;
    width: 100%;
    // align-items: flex-start;
    justify-content: space-between; 
  //  margin-left: -1px;
  }

  label{
    color: #909090;
  }
	.fld-error .msg-error  {
		display: block;
	}
	.msg-error {
		display: none;
	}

  .containerButton{
    display: flex;
    justify-content: flex-end;
  }

  button{
    background-color: #8A2BE2;
    color: #fff;
    width: 20rem;
    height: 3rem;
    /* text-transform: uppercase; */
    font-weight: bold;
    border-radius: 0.2rem;
    margin-top: 0.1rem;
  }
</style>

