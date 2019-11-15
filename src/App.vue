<template>
   <div>
      <clock class="clock" location="TOKYO" :diff="0"/>
      <clock class="clock" location="NY" :diff="-14"/>
      <clock class="clock" location="LA" :diff="-17"/>
      <clock class="clock" location="UK" :diff="-9"/>
      <clock class="clock" location="BRAZIL" :diff="-12"/>
      <clock class="clock" location="SYDNEY" :diff="1"/>
      <clock class="clock" location="DUBAI" :diff="-5"/>
      <clock class="clock" location="JOHANNESBURG" :diff="-7"/>
    </div>
</template>

<script>
import Clock from "@/components/Clock"
 
export default {
  components: {
    Clock
  }
}
</script>

<style scoped>
  .clock {
    width: 80%;
    max-width: 500px;
    margin: 30px auto;
  }

</style>
<style>
  html {
    font-size: 62.5%;
  }
  body {
    margin: 0;
  }
  p {
    margin: 0;
  }
</style>
