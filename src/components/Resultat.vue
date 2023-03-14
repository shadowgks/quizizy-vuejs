<template>
    <!-- resultat -->
    <div class="box_resultat">
        <div class="resultat_header">
            <i class="fa-solid fa-ranking-star"></i>
        </div>
        <div class="resultat_body">
            <div class="name_user">
                <h4>saad</h4>
            </div>
            <div class="text_finish">
                <span>Completed the Quiz!</span>
            </div>
            <div class="score">
                <p>You got <span>{{score}}</span> out of <span>{{lenght_data}}</span></p>
            </div>
        </div>
        <div class="resultat_footer">
            <button class="quit">Quit Quiz</button>
            <button class="continue">Your Ansewer</button>
        </div>
    </div>
</template>

<script>
export default {
    props : ['lenght_data','score'],
}
</script>

<style></style>