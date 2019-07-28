<template>
    <button class="g-button"  :class="{[`icon-${iconPosition}`]:true}">
        <g-icon v-if="icon" :name="icon"></g-icon>
        <div class="content">
            <slot></slot>
        </div>
    </button>
</template>

<script>
    export default {
        props:{
            icon:{},
            iconPosition:{
                type:String,
                default:'left',
                validator(value){
                    return value === 'left' || value === 'right';
                    // 此处是属性的检查器，返回false会报错
                }
            }
        }
    }
</script>

<style lang="scss">
    .g-button {
        font-size: var(--font-size);
        height: var(--button-height);
        padding: 0 1em;
        border-radius: var(--border-radius);
        border: 1px solid var(--border-color);
        background: var(--button-bg);
        display: inline-flex;
        justify-content: center;
        align-items: center;
        vertical-align: middle;
        &:hover {
            border-color: var(--border-color-hover);
        }

        &:active {
            background-color: var(--button-active-bg);
        }

        &:focus {
            outline: none;
        }
        > .content{
            order:2
        }
        > .icon{
            order:1;
            margin-right: .3em;
        }
        &.icon-right{
            > .content{
                order:1
            }
            > .icon{
                order:2;
                margin-left: .3em;
                margin-right: 0;
            }
        }
        /*&表示当前的选择器*/
        /*>表示选择子代，孙代不选择*/
    }

</style>