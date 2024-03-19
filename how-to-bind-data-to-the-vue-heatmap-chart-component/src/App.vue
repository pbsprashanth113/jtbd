<script setup>
import { provide } from 'vue';
import { HeatMapComponent as EjsHeatmap, Adaptor,  Tooltip, Legend } from "@syncfusion/ej2-vue-heatmap";
import situation_needs_vs_posts  from './assets/situation_needs_vs_posts.json' 
import situations_vs_posts  from './assets/situation_vs_posts_heatmap.json' 
import situation_need_vs_situation_need  from './assets/cosine_sim_matrix_situation_need_vs_situation_need.json' 

const posts = situation_needs_vs_posts["posts"]
const situation_needs = situation_needs_vs_posts["situation_needs"]
const situations = situations_vs_posts["situation"]
const _situation_need = situation_need_vs_situation_need["situation_needs"]

const xAxis = { labels : posts, visible: true}
const yAxis_situations = { labels : situations, visible: true}
const yAxis = { labels : situation_needs, visible: true}
const situation_need_vs_situation_need_xAxis_yAxis= { labels : _situation_need, visible: true}

const paletteSettings = {
            palette: [
               { value: 0, color: '#FFA500' }, { value: 50, color: '#00FF00' }, { value: 100, color: '#FF0000' }
            ],
            type: "Gradient"
        }

const dataSourceSettings ={
    adaptorType : 'Cell',
    isJsonData : false,
}
const cellSettings = {
    // tileType: "Bubble",
    bubbleType: "SizeAndColor",
}


let template =  '<div style="background-color: white; width: 500px; padding-bottom: 2px">'+
                        '<div>'+
                            '<div>'+
                                    '${yLabel}' +
                                '</div>'+
                            '</div>'+
                        '<div>${xLabel}</div>'+
                    '</div>';
                
const tooltipSettings = {
            fill: '#696295',
            textStyle: {
                color: '#FFFFFF',
                size: '12px'
            },
             border: {
                width: 2,
                color: '#F0C27B'
            },
            template: template
        }
provide('heatmap', [Adaptor, Tooltip, Legend])

const showTooltip = true

</script>
<template>
        <div style="padding-top: 10pt;">
                  <h1>Situation and Needs Vs Posts Chart</h1>
                  <ejs-heatmap id="situation_needs_vs_posts" :dataSource="situation_needs_vs_posts['cosine_sim_matrix']" :xAxis="xAxis" :yAxis="yAxis" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
        <div style="padding-top: 10pt;">
                  <h1>Situation vs Posts Chart</h1>
                  <ejs-heatmap   id="situations_vs_posts" :dataSource="situations_vs_posts['cosine_sim_matrix']" :xAxis="xAxis" :yAxis="yAxis_situations" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
        <div style="padding-top: 10pt;">
                  <h1>Situation Needs vs Situation Needs</h1>
                  <ejs-heatmap   id="situation_need_vs_situation_need" :dataSource="situation_need_vs_situation_need['cosine_sim_matrix']" :xAxis="xAxis" :yAxis="situation_need_vs_situation_need_xAxis_yAxis" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
</template>
<style scoped>
    table,
    th,
    td {
        border: 1px solid rgb(105, 105, 105);
        border-collapse: collapse;
    }
</style>
<style>
</style>
