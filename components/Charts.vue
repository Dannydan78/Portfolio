<template>
     <div ref="chartContainer" class="chart-container mt-8"></div>
</template>

<script setup>

import { ref, onMounted, onBeforeUnmount, nextTick } from 'vue';
import * as echarts from 'echarts';

// Référence pour le chart
const chartContainer = ref(null);
let chart = null;

// Configuration du chart
const initChart = () => {
  if (chartContainer.value) {
    nextTick(() => {
      chart = echarts.init(chartContainer.value);
      
      const option = {

        color: [
          '#37A2FF', 
          '#8A2BE2',
          '#19f6e8',
          '#f619ef',
          '#3b09d4',
        
        ],

        title: {
          text: 'Missions réalisées',
          subtext: '',
          left: 'center',
          textStyle: {
            color: '#fff',
            fontSize: 24,
            fontWeight: 'bold'
          },
          subtextStyle: {
            color: '#ccc',
            fontSize: 14
          }
        },

        tooltip: {
          trigger: 'item',
          formatter: function(params) {
            return params.data.tooltipText;
          },
          backgroundColor: 'rgba(0,0,0,0.7)',
          // borderColor: '#fff',
          borderWidth: 1,
          textStyle: {
            color: '#fff'
          }
        },

        // legend: {
        //   bottom: 10,
        //   left: 'center',
        //   data: ['Laravel', 'Vue.js', 'MySql', 'Docker'],
        //   textStyle: {
        //     color: '#fff',
        //     fontSize: 14
        //   },
        //   itemWidth: 25,
        //   itemHeight: 14
        // },

        series: [
          {
            name: 'Frameworks',
            type: 'pie',
            radius: '65%',
            center: ['50%', '50%'],
            selectedMode: 'single',
            data: [
              { 
                value: 1548, 
                name: 'Laravel',
                tooltipText: `
                  <strong>Laravel</strong><br/>
                  • Développement API REST<br/>
                  • Gestion de base de données<br/>
                  • Script pour transporter des données<br/>
                  • Tests unitaires
                `,
                itemStyle: {
                  borderRadius: 2,
                  borderWidth: 2
                }
              },
              { 
                value: 1450, 
                name: 'Vue.js',
                tooltipText: `
                  <strong>Vue.js</strong><br/>
                  • Composants réutilisables<br/>
                  • State management<br/>
                  • Interfaces réactives<br/>
                  • Animations
                `
              },
              { 
                value: 510, 
                name: 'Sql',
                tooltipText: `
                  <strong>SQL</strong><br/>
                  • Requêtes complexes<br/>
                  • Optimisation<br/>
                  • Modélisation<br/>
                `
              },
              { 
                value: 234, 
                name: 'Docker',
                tooltipText: `
                  <strong>Docker</strong><br/>
                  • Conteneurisation<br/>
                  • Docker-compose<br/>
                  • Déploiement
                `
              },
            ],
            emphasis: {
              itemStyle: {
                shadowBlur: 10,
                shadowOffsetX: 0,
                shadowColor: 'rgba(0, 0, 0, 0.5)',
                borderColor: '#fff',
                borderWidth: 2
              }
            },
            label: {
              show: true,
              color: '#fff',
              formatter: '{b}',
              fontSize: 14
            },
            labelLine: {
              show: true,
              length: 15,
              length2: 10,
              lineStyle: {
                color: '#fff'
              }
            },
            itemStyle: {
              borderRadius: 2,
              borderWidth: 2
            }
          }
        ]
      };

      chart.setOption(option);
    });
  }
};

// Gestion du redimensionnement
const handleResize = () => {
  if (chart) {
    chart.resize();
  }
};

onMounted(() => {
  // Initialisation du chart
  initChart();
  
  // Ajout de l'écouteur de redimensionnement
  window.addEventListener('resize', handleResize);
  
});

onBeforeUnmount(() => {
  // Nettoyage du chart
  if (chart) {
    chart.dispose();
  }
  window.removeEventListener('resize', handleResize);
});
</script>


<style scoped>
.chart-container {
  width: 100%;
  height: 400px;
  position: relative;
}
</style>