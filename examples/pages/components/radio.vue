<template>
    <div id="radio">
        <navbar>单选框</navbar>

        <div class="content">
            <card>
                <div name="header">单选框列表</div>
                <div name="content">
                    <radio v-model="value1" :origin-value="item" v-for="(item, index) in listA" key="index" inline>{{item}}</radio>
                </div>
                <div name="footer">
                    <span>选中的项:</span>
                    <span> {{ value1 }} </span>
                </div>
            </card>

            <card>
                <div name="header">可禁用的单选框列表</div>
                <div name="content">
                    <radio v-model="value2" :origin-value="item" v-for="(item, index) in listA" key="index">{{item}}</radio>
                    <radio v-model="value2" origin-value="选项D" disabled>选项D</radio>
                </div>
                <div name="footer">
                    <span>选中的项:</span>
                    <span> {{ value2 }} </span>
                </div>
            </card>

            <card>
                <div name="header">支持关联复选框列表的单选框</div>
                <div name="content" class="group-box">
                    <radio v-model="value3" origin-value="A" :child-values="listA" :child-checked="list1" v-sync:child="list1">选择分组A</radio>
                    <checkbox v-model="list1" :origin-value="item" v-for="(item, index) in listA" :key="'A' + index" class="box-item">{{item}}</checkbox>

                    <div class="separator"></div>

                    <radio v-model="value3" origin-value="B" :child-values="listB" :child-checked="list2" v-sync:child="list2">选择分组B</radio>
                    <checkbox v-model="list2" :origin-value="item" v-for="(item, index) in listB" :key="'B' + index" class="box-item">{{item}}</checkbox>
                </div>
                <div name="footer">
                    <span>选中的项:</span>
                    <span> {{ value3 }} </span>
                </div>
            </card>
        </div>
    </div>
</template>

<script type="es6">
    import { Navbar, Card, Radio, Checkbox } from 'vmc';

    export default {
        components: {
            Navbar,
            Card,
            Radio,
            Checkbox
        },
        data() {
            return {
                listA: ['选项A', '选项B', '选项C'],
                listB: ['选项1', '选项2', '选项3', '选项4'],
                list1: [],
                list2: [],
                value1: '选项A',
                value2: '选项D',
                value3: 'A'
            }
        }
    }
</script>

<style rel="stylesheet/less" lang="less">
    #radio {
        .content {
            height: 100%;
            box-sizing: border-box;
            overflow: auto;
            background: #eeeeee;

            .group-box {
                .box-item {
                    margin-left: 10px;
                }

                .separator {
                    height: 15px;
                }
            }
        }
    }
</style>
