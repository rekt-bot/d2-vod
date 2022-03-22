<template>
  <div>
    <h1>{{ msg }}</h1>
    <FormulateForm v-model="formValues" @change="handleSubmit" class="form-container container">
      <div>
        <FormulateInput 
        name="guardian1" 
        v-model="guardian1.name" 
        label="Guardian 1"
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian1.new"
          name="guardian1_new"
          label="Inexperienced"
        />
      </div>
      <div>
        <FormulateInput 
        name="guardian2" 
        v-model="guardian2.name" 
        label="Guardian 2"
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian2.new"
          name="guardian2_new"
          label="Inexperienced"
        />
      </div>

      <div>
        <FormulateInput 
        name="guardian3"
        v-model="guardian3.name" 
        label="Guardian 3" 
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian3.new"
          name="guardian3_new"
          label="Inexperienced"
        />
      </div>
      <div>
        <FormulateInput 
        name="guardian4" 
        v-model="guardian4.name" 
        label="Guardian 4"
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian4.new"
          name="guardian4_new"
          label="Inexperienced"
        />
      </div>
      <div>
        <FormulateInput 
        name="guardian5" 
        v-model="guardian5.name" 
        label="Guardian 5"
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian5.new"
          name="guardian5_new"
          label="Inexperienced"
        />
      </div>
      <div>
        <FormulateInput 
        name="guardian6"
        v-model="guardian6.name" 
        label="Guardian 6" 
        />
        <FormulateInput 
          type="checkbox"
          v-model="guardian6.new"
          name="guardian6_new"
          label="Inexperienced"
        />
      </div>
    </FormulateForm>
    <div class="container groups">
      <div class="group">
        <h2>Acquisition (Totems)</h2>
        <dl>
          <dt>Team Dark</dt>
            <dd :style="guardian1.new ? 'color: red;' : ''">Totem: {{ guardian1.name }}</dd>
            <dd :style="guardian2.new ? 'color: red;' : ''">Runner: {{ guardian2.name }}</dd>

          <dt>Team Mid</dt>
            <dd :style="guardian3.new ? 'color: red;' : ''">Totem: {{ guardian3.name }}</dd>
            <dd :style="guardian4.new ? 'color: red;' : ''">Runner: {{ guardian4.name }}</dd>

          <dt>Team Light</dt>
            <dd :style="guardian5.new ? 'color: red;' : ''">Totem: {{ guardian5.name }}</dd>
            <dd :style="guardian6.new ? 'color: red;' : ''">Runner: {{ guardian6.name }}</dd>
        </dl>
      </div>
      <div class="group">
        <h2>Collection (Caretaker)</h2>
        <dl>
          <dt>Totem Team</dt>
            <dd :style="guardian1.new ? 'color: red;' : ''">First: {{ guardian1.name }}</dd>
            <dd :style="guardian2.new ? 'color: red;' : ''">Second: {{ guardian2.name }}</dd>

          <dt>Add Clear</dt>
            <dd :style="guardian3.new ? 'color: red;' : ''">{{ guardian3.name }}</dd>
            <dd :style="guardian4.new ? 'color: red;' : ''">{{ guardian4.name }}</dd>

          <dt>Stunners</dt>
            <dd :style="guardian5.new ? 'color: red;' : ''">{{ guardian5.name }}</dd>
            <dd :style="guardian6.new ? 'color: red;' : ''">{{ guardian6.name }}</dd>
        </dl>
      </div>
      <div class="group">
        <h2>Exhibition (Relics)</h2>
        <dl>
          <dt>Room 1</dt>
            <dd :style="guardian1.new ? 'color: red;' : ''">Shard: {{ guardian1.name }}</dd>

          <dt>Room 2</dt>
            <dd :style="guardian2.new ? 'color: red;' : ''">Shard: {{ guardian2.name }}</dd>
            <dd :style="guardian3.new ? 'color: red;' : ''">Relic: {{ guardian3.name }}</dd>

          <dt>Room 3</dt>
            <dd :style="guardian4.new ? 'color: red;' : ''">Shard: {{ guardian4.name }}</dd>
            <dd :style="guardian5.new ? 'color: red;' : ''">Relic: {{ guardian5.name }}</dd>
            <dd :style="guardian6.new ? 'color: red;' : ''">Blight: {{ guardian6.name }}</dd>
            
          <dt>Room 4</dt>
            <dd :style="guardian2.new ? 'color: red;' : ''">Shard: {{ guardian2.name }}</dd>
            <dd :style="guardian3.new ? 'color: red;' : ''">Relic: {{ guardian3.name }}</dd>
            <dd :style="guardian1.new ? 'color: red;' : ''">Blight: {{ guardian1.name }}</dd>
        </dl>
      </div>
      <div class="group">
        <h2>Dominion (Rhulk)</h2>
        <dl>
          <dt>Dunkers</dt>
            <dd :style="guardian1.new ? 'color: red;' : ''">First: {{ guardian1.name }}</dd>
            <dd :style="guardian2.new ? 'color: red;' : ''">Second: {{ guardian2.name }}</dd>

          <dt>Passers</dt>
            <dd :style="guardian3.new ? 'color: red;' : ''">First: {{ guardian3.name }}</dd>
            <dd :style="guardian4.new ? 'color: red;' : ''">Second: {{ guardian4.name }}</dd>

          <dt>Adds / Callouts</dt>
            <dd :style="guardian5.new ? 'color: red;' : ''">Left: {{ guardian5.name }}</dd>
            <dd :style="guardian6.new ? 'color: red;' : ''">Right: {{ guardian6.name }}</dd>
        </dl>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FormulateTest',
  props: {
    msg: String
  },
  data() {
    return {
      guardian1: {
        name: '',
        new: false
      },
      guardian2: {
        name: '',
        new: false
      },
      guardian3: {
        name: '',
        new: false
      },
      guardian4: {
        name: '',
        new: false
      },
      guardian5: {
        name: '',
        new: false
      },
      guardian6: {
        name: '',
        new: false
      },
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.container {
	max-width: 1260px;
	margin: 0 auto 3rem;
	text-align: left;
	display: flex;
	flex-wrap: wrap;
	justify-content: space-between;
}

.form.container input {
	margin-bottom: 1rem;
}

dt {
  margin: 2rem 0 1rem;
  font-weight: bold;
  text-decoration: underline;
}

dd {
  margin-left: 1rem;
  margin-bottom: 0.5rem;
}

input[type=checkbox] {
  float: left;
}

[data-type=checkbox] + label {
  font-size: 14px;
}

.sherpa {
  color: red;
}
</style>
