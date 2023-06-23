<template>
    <div class="container mx-auto">
        <canvas id="chart"></canvas >
        <hr>
        <div class="mb-4">
            <div class="row">
                <div class="col-10"></div>
                <div class="col-2">
                    <router-link
                    to="create/movie"
                    class="btn btn-success"
                    aria-current="page"
                >
                Добавить фильм
                </router-link>
                </div>
            </div>
            <div class="mb-2 mt-4">
                <table class="table">
                    <thead>
                        <tr>
                            <th scope="col">НАЗВАНИЕ</th>
                            <th scope="col">РЕЙТИНГ</th>
                            <th scope="col">ГОД ВЫХОДА</th>
                            <th scope="col">РЕЖИСЁР</th>
                            <th scope="col">ЖАНР</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr
                            v-for="el in list"
                            v-bind:key="el"
                            >
                            <th scope="row">1</th>
                            <td>{{el.name}}</td>
                            <td>{{el.rating}}</td>
                            <td>{{el.release}}</td>
                            <td>{{el.director}}</td>
                            <td>{{el.genre}}</td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>
</template>

<script>
    import Chart from 'chart.js/auto';
    import { getRelativePosition } from 'chart.js/helpers';


    export default{
        data()
        {
            return {
                list: [
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          },
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          },
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          },
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          },
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          },
          {
            name: "Аватар",  
            rating: 10.2, 
            release: 1985,
            director: "Михалков Н.С",
            genre: "Детектив"
          }
        ]

            }
        },
        methods: {
            diagram: () => {
                const chart = new Chart(document.querySelector('#chart'),
                {
                    type: 'bar',
                    data: {
                        labels: ['Ужасы', 'Док. фильмы', 'Комедии', 'Боевик', 'Меллодрамы', 'Триллер'],
                        datasets: [{
                            label: 'График популярности жанров',
                            data: [12, 19, 9, 5, 20, 13],
                            borderWidth: 1
                        }]
                    },
                    options: {
                        onClick: (e) => {
                        const canvasPosition = getRelativePosition(e, chart);

                        // Substitute the appropriate scale IDs
                        const dataX = chart.scales.x.getValueForPixel(canvasPosition.x);
                        const dataY = chart.scales.y.getValueForPixel(canvasPosition.y);
                        }
                    }
                });
                
            }
        },
        mounted()
        {
            this.diagram()
        }
    }
</script>