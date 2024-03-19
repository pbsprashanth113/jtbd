<script setup>
import { provide } from 'vue';
import { HeatMapComponent as EjsHeatmap, Adaptor,  Tooltip, Legend } from "@syncfusion/ej2-vue-heatmap";
import situation_need_vs_post  from './assets/situation_needs_vs_posts.json' 
import situation_vs_post  from './assets/situation_vs_posts_heatmap.json' 
import situation_need_vs_situation_need  from './assets/cosine_sim_matrix_situation_need_vs_situation_need.json' 
import situation_vs_situation from './assets/cosine_sim_matrix_situation_vs_situation.json' 

const situation_need_vs_posts__posts = situation_need_vs_post["posts"]
const situation_need_vs_posts__situation_needs = situation_need_vs_post["situation_needs"]
const situation_vs_posts_posts = situation_vs_post["posts"]
const situation_vs_posts_situation = situation_vs_post["situation"]
const _situation_need_vs_situation_need = situation_need_vs_situation_need["situation_needs"]
const _situation_vs_situation = situation_vs_situation["situation"]

// const situation_need_vs_posts_xAxis = { labels : posts, visible: true}
// const situation_need_vs_posts_yAxis = { labels : posts, visible: true}

// const situation_yAxis = { labels : situations, visible: true}
// const situation_need_yAxis = { labels : situation_needs, visible: true}
// const situation_need_vs_situation_need_yAxis= { labels : situation_need, visible: true}

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
                  <h1>Situation and Needs Vs Posts </h1>
                  <ejs-heatmap id="situation_needs_vs_posts" :dataSource="situation_need_vs_post['cosine_sim_matrix']" :xAxis="{ labels : situation_need_vs_posts__posts, visible: true}" :yAxis="{ labels : situation_need_vs_posts__situation_needs, visible: true}" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
        <div style="padding-top: 10pt;">
                  <h1>Situation vs Posts </h1>
                  <ejs-heatmap   id="situations_vs_posts" :dataSource="situation_vs_post['cosine_sim_matrix']" :xAxis="{ labels : situation_vs_posts_posts, visible: true}" :yAxis="{ labels :  situation_vs_posts_situation, visible: true}" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
        <div style="padding-top: 10pt;">
                  <h1>Situation Need vs Situation Need</h1>
                  <ejs-heatmap   id="situation_need_vs_situation_need" :dataSource="situation_need_vs_situation_need['cosine_sim_matrix']" :xAxis="{ labels : _situation_need_vs_situation_need, visible: true}" :yAxis="{ labels : _situation_need_vs_situation_need, visible: true}" 
                  height="4000px" width="4000px"   :paletteSettings="paletteSettings"  :tooltipSettings="tooltipSettings"></ejs-heatmap>
        </div>
        <div style="padding-top: 10pt;">
                  <h1>Situation  vs Situation </h1>
                  <ejs-heatmap   id="situation_vs_situation" :dataSource="situation_vs_situation['cosine_sim_matrix']" :xAxis=" { labels : _situation_vs_situation , visible: true}" :yAxis="{ labels : _situation_vs_situation , visible: true}" 
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
