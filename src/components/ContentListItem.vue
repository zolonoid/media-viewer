<template>
    <div class="content-list-item" @click.stop="clickHandler">
        <div class="content-list-item__preview"
             :style="{ backgroundImage: `$url('${preview}')` }"></div>
        <div class="content-list-item__title">
            {{ title }}
        </div>
        <div class="content-list-item__icon">
            <svg v-if="type === 'audio'" fill="#ffffff" viewBox="0 0 512 512" enable-background="new 0 0 512 512"
                 id="Layer_1"
                 version="1.1" xml:space="preserve" xmlns="http://www.w3.org/2000/svg"
                 xmlns:xlink="http://www.w3.org/1999/xlink" stroke="#ffffff">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
                <g id="SVGRepo_iconCarrier">
                    <g>
                        <g>
                            <path
                                  d="M159.465,399.25c-25.093,0-45.508-20.415-45.508-45.509s20.415-45.509,45.508-45.509c25.094,0,45.51,20.415,45.51,45.509 S184.559,399.25,159.465,399.25z M159.465,328.232c-14.065,0-25.508,11.443-25.508,25.509s11.442,25.509,25.508,25.509 c14.066,0,25.51-11.443,25.51-25.509S173.531,328.232,159.465,328.232z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M194.975,363.741c-5.522,0-10-4.478-10-10V184.25c0-4.354,2.816-8.207,6.965-9.528l193.068-61.5 c3.04-0.968,6.36-0.428,8.937,1.455s4.099,4.883,4.099,8.073v169.491c0,5.522-4.478,10-10,10s-10-4.478-10-10V136.431 L204.975,191.56v162.182C204.975,359.264,200.497,363.741,194.975,363.741z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M352.535,337.75c-25.094,0-45.51-20.415-45.51-45.509s20.416-45.509,45.51-45.509c25.093,0,45.508,20.415,45.508,45.509 S377.628,337.75,352.535,337.75z M352.535,266.732c-14.066,0-25.51,11.443-25.51,25.509s11.443,25.509,25.51,25.509 c14.065,0,25.508-11.443,25.508-25.509S366.601,266.732,352.535,266.732z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M194.974,231.92c-4.182,0-8.08-2.644-9.481-6.827c-1.754-5.236,1.069-10.904,6.307-12.658l193.068-64.666 c5.234-1.752,10.904,1.07,12.658,6.307s-1.069,10.904-6.307,12.658L198.15,231.399C197.098,231.752,196.026,231.92,194.974,231.92 z">
                            </path>
                        </g>
                    </g>
                </g>
            </svg>
            <svg v-else-if="type === 'image'" fill="#ffffff" viewBox="0 0 512 512" enable-background="new 0 0 512 512"
                 id="Layer_1"
                 version="1.1" xml:space="preserve" xmlns="http://www.w3.org/2000/svg"
                 xmlns:xlink="http://www.w3.org/1999/xlink" stroke="#ffffff">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
                <g id="SVGRepo_iconCarrier">
                    <g>
                        <g>
                            <path
                                  d="M453,395.5H59c-5.522,0-10-4.478-10-10v-259c0-5.522,4.478-10,10-10h394c5.522,0,10,4.478,10,10v259 C463,391.022,458.522,395.5,453,395.5z M69,375.5h374v-239H69V375.5z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M294.009,395.502c-3.524,0-6.941-1.867-8.765-5.171l-58.703-106.4L64.614,393.775c-4.569,3.102-10.789,1.91-13.89-2.661 s-1.909-10.789,2.661-13.89l171-116c2.328-1.579,5.21-2.105,7.945-1.449c2.734,0.655,5.066,2.432,6.425,4.894l64,116 c2.668,4.836,0.91,10.919-3.925,13.587C297.299,395.101,295.643,395.502,294.009,395.502z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M453.002,395.5c-2.68,0-5.351-1.07-7.321-3.186L343.604,282.676l-75.876,53.021c-4.525,3.164-10.761,2.057-13.925-2.47 c-3.163-4.526-2.058-10.761,2.47-13.925l83-58c4.085-2.854,9.649-2.266,13.047,1.383l108,116 c3.763,4.042,3.537,10.37-0.505,14.134C457.888,394.612,455.441,395.5,453.002,395.5z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M245.5,232.666c-19.575,0-35.5-15.925-35.5-35.5s15.925-35.5,35.5-35.5s35.5,15.925,35.5,35.5 S265.075,232.666,245.5,232.666z M245.5,181.666c-8.547,0-15.5,6.953-15.5,15.5s6.953,15.5,15.5,15.5s15.5-6.953,15.5-15.5 S254.047,181.666,245.5,181.666z">
                            </path>
                        </g>
                    </g>
                </g>
            </svg>
            <svg v-else-if="type === 'video'" fill="#ffffff" viewBox="0 0 512 512" enable-background="new 0 0 512 512"
                 id="Layer_1"
                 version="1.1" xml:space="preserve" xmlns="http://www.w3.org/2000/svg"
                 xmlns:xlink="http://www.w3.org/1999/xlink" stroke="#ffffff">
                <g id="SVGRepo_bgCarrier" stroke-width="0"></g>
                <g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g>
                <g id="SVGRepo_iconCarrier">
                    <g>
                        <g>
                            <path
                                  d="M434.269,334.688c-1.055,0-2.115-0.167-3.141-0.506l-110.551-36.58c-4.094-1.354-6.858-5.181-6.858-9.494v-55.275 c0-4.052,2.445-7.704,6.192-9.247l110.551-45.521c3.086-1.271,6.6-0.918,9.372,0.938c2.772,1.856,4.436,4.973,4.436,8.309v137.376 c0,3.21-1.542,6.226-4.144,8.106C438.399,334.042,436.346,334.688,434.269,334.688z M333.719,280.884l90.551,29.962V202.245 l-90.551,37.285V280.884z">
                            </path>
                        </g>
                        <g>
                            <path
                                  d="M311.719,347.962H89.73c-12.131,0-22-9.869-22-22V186.038c0-12.131,9.869-22,22-22h221.988c12.131,0,22,9.869,22,22 v139.924C333.719,338.093,323.85,347.962,311.719,347.962z M89.73,184.038c-1.103,0-2,0.897-2,2v139.924c0,1.103,0.897,2,2,2 h221.988c1.103,0,2-0.897,2-2V186.038c0-1.103-0.897-2-2-2H89.73z">
                            </path>
                        </g>
                    </g>
                </g>
            </svg>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        type: String,
        preview: String,
        title: String
    },
    emits:[
        "itemClick"
    ],
    methods: {
        clickHandler(){
            this.$emit("itemClick");
        }
    },
}
</script>

<style lang="scss">
.content-list-item {
    position: relative;
    aspect-ratio: 4 / 3;

    &__preview {
        height: calc(100% - 2em);
        background-size: 100% 100%;
    }

    &__title {
        height: 2em;
        margin: 0;
        /* Убираем внешний отступ */
        -webkit-line-clamp: 2;
        /* Число отображаемых строк */
        display: -webkit-box;
        /* Включаем флексбоксы */
        -webkit-box-orient: vertical;
        /* Вертикальная ориентация */
        overflow: hidden;
        /* Обрезаем всё за пределами блока */
    }

    &__icon {
        position: absolute;
        top: 5%;
        left: 5%;
        width: 64px;
        height: 64px;
    }
}
</style>