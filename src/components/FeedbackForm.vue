<template>
  <form class="feedback">
    <label>Name</label>
    <input type="text" required placeholder="Ur name" />
    <label>Your ideas</label>
    <textarea
      placeholder="Tell us what you'd like to see...Max length - 300 characters"
      maxlength="300"
    ></textarea>
    <label>First time?</label>
    <select v-model="status">
      <option value="new">I am new</option>
      <option value="regular">I am a member</option>
    </select>
    <div class="submit"><button>Send</button></div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      message: "message here",
      status: "new",
    };
  },
};
</script>

<style scoped>
.feedback {
  padding: 20px 40px;
  max-width: 50%;
  min-width: fit-content;
  text-align: left;
  justify-self: center;
  border-radius: 10px;
  margin: 30px;
  background: rgba(233, 227, 255, 50%);
}
textarea {
  margin: 10px 0;
  display: block;
  resize: none;
  width: 400px;
  height: 200px;
  border: none;
  border-bottom: 1px solid var(--accent);
}
label {
  display: inline-block;
  letter-spacing: 1px;
  font-weight: bold;
  font-size: 0.8em;
}
input,
select {
  height: 30px;
  width: 100%;
  display: block;
  margin: 10px 0;
  border: none;
  border-bottom: 1px solid var(--accent);
  padding: 2px;
}
button {
  cursor: pointer;
  border-radius: 20px;
  color: var(--background);
  background-color: var(--accent);
  padding: 10px;
  border: none;
  font-weight: bold;
}
.submit {
  text-align: center;
  margin-top: 1em;
}
</style>
