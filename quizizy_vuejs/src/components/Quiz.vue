<script>
    import data from "../assets/js/data/newData.json";
export default {
    components: {data},
    data(){
        return{
            myJson: data
        }
    }
}
</script>

<template>
    <!-- quiz -->
    <div class="box_quiz">
        <!-- {{myJson[0]['answer'][0]}} -->
        <div class="quiz_header">
            <h3>Quiz of AWS</h3>
            <div class="time">
                <span class="text_time">Time left</span>
                <span class="count">30</span>
            </div>
        </div>
        <div class="quiz_body">
            <div class="title">
                <!-- <h2>Why is AWS more economical than traditional data centers for applications with varying compute
                    workloads?</h2> -->
            </div>
            <div class="questions">
                <div>
                        <div class="question correct">
                            <p>Amazon EC2 costs are billed on a monthly basis.</p><i class="fa-regular fa-circle-check good"></i>
                        </div>
                        <div class="question incorrect">
                            <p>Users retain full administrative access to their Amazon EC2 instances.</p><i class="fa-regular fa-circle-xmark faild"></i>
                        </div>
                        <div class="question">
                            <p>Amazon EC2 instances can be launched on demand when needed.</p>
                        </div>
                        <div class="question">
                            <p>Users can permanently run enough instances to handle peak workloads.</p>
                        </div>
                </div>
            </div>
        </div>
        <div class="quiz_footer">
            <p><span class="step">1</span> of <span class="all">10</span> Questions</p>
            <div>
                <button class="submit">Submit</button>
                <button class="next">Next</button>
            </div>
        </div>
    </div>
</template>

<style></style>