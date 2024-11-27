<script setup lang="ts">
</script>
<template>
  
    <div class="welcome">
    
      <p class="text-display-2">
        <br>
        Potential Member Information
      </p>
      <br>
    
   <div class="info">
    <p>*Skill evaluations for Fall 2024 are now closed. Check back in the spring for new info session dates.</p>
  
  
    <br>
    <br>
   
    <NuxtLink to="https://rsconnect.recsports.ufl.edu/program/GetProgramDetails?courseId=b78354d4-26b8-4a12-8ff3-af85564e3bc4"><button style="background-color:  #1243e5; color: white;   border-radius: 10px; padding: 5px; padding-left:10px; padding-right:10px;"><button:hover style="background-color: antiquewhite;"><p style= "font-size: 20px"><b>Sports Club Waiver</b></p></button:hover></button></NuxtLink>
    
        <br><br>
    
    <p><b>Skill Evaluations: What to Bring</b></p>
    <br>
    <p>
        UF ID
    </p>
    <p>
        Water
    </p>
    <p>
        Athletic clothing
    </p>
    <p>
        Shin guards
    </p>
    <p>
        Cleats
    </p>
    <br>
    <p style="text-indent: 40px">*Please arrive at the field 20 minutes before the session. </p>
  </div>
    </div>
 
</template>

<style>
.text-display-2{
  text-align: center;
  color:#FA4616;
  text-shadow:
    -1px -1px 0 #fff,
    1px -1px 0 #fff,
    -1px 1px 0 #fff,
    1px 1px 0 #fff;  
  
}
  .welcome{
    align-items: center;
    text-indent: 40px;
    background-image: url(https://static.vecteezy.com/system/resources/previews/028/622/004/non_2x/soccer-field-in-flat-style-football-stadium-illustration-on-isolated-background-sport-plan-sign-business-concept-vector.jpg);
    background-size:cover;
    min-height: 800px;
}
  

  .info{
    text-indent: 20px;
    margin-left: 20px;
    margin-right: 800px;
    font-weight: bold;
    background-color: black;
    min-height: 400px;
    text-align: center;
    color:white;
    padding: 50px;
    border-radius: 20px;
    margin-left: 500px;
    margin-right: 500px;
    margin-top:100px;
  }
.home{
  color:black;
}
.memberInfo{
  color:#FA4616;
}


</style>