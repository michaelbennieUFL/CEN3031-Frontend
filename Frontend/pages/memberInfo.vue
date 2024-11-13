<script setup lang="ts">
</script>
<template>
    <div class="welcome">
    
      <p class="text-display-2">
        Potential Member Information
      </p>
    </div>
    <div class="info">
    <p>*Skill evaluations for Fall 2024 are now closed. Check back in the spring for new info session dates!</p>
    </div>
    <br>
    <br>
    <div class="general">
    <NuxtLink to="https://rsconnect.recsports.ufl.edu/program/GetProgramDetails?courseId=b78354d4-26b8-4a12-8ff3-af85564e3bc4"><b><u><p style= "font-size: 30px">Sports Club Waiver</p></u></b></NuxtLink>
        <br><br>
    <p><b>Skill Evaluations: What to Bring</b></p>
    <br>
    <li>
        UF ID
    </li>
    <li>
        Water
    </li>
    <li>
        Athletic clothing
    </li>
    <li>
        Shin guards
    </li>
    <li>
        Cleats
    </li>
    <p style="text-indent: 40px">*Please arrive at the field 20 minutes before the session! </p>
    </div>
</template>

<style>
 .welcome{
  background-image: url("images/soccer_pattern.jpg");
  color: #d77608;
  text-shadow: 0 0 4px #1243e5, 0 0 4px #1243e5;
  border: 4px solid black;
  margin: 20px;
  padding: 50px;
  text-align: center;
  border-radius: 20px;

  }
  .general{
    text-indent: 40px;
  }
  .info{
    text-indent: 40px;
    background-color: #d77608;
    margin-left: 20px;
    margin-right: 800px;
    font-weight: bold;
  }
</style>