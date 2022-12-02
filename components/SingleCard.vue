<template>
    <div style="background-color:gainsboro ;margin: 10px 0; flex-direction: column; border-radius: 10px;" class="center">
        <div style="width: 90%; display: flex; flex-direction: row; justify-content: space-between;">
            <div style="width: 10%;">{{person.id}}</div>
            <div style="width: 80%;">{{person.first_name}}</div>
        </div>

        <div style="width: 90%; display: flex; flex-direction: row; justify-content: space-between;">
            <div>{{person.email}}</div>
            <div>{{person.gender}}</div>
        </div>

    </div>
</template>

<script>
export default {
    props: ['person']

}
</script>

<style>
.center{
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>