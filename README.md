# Dash-APC

import pandas as pd
import plotly.express as px 

df = pd.read_csv('imdb_top_1000.csv')
df.head(20)

lista = df.values.tolist()

ratings_printed = []
nomes_filme = []
for i in lista:
  if i[6] not in ratings_printed:
    ratings_printed.append(i[6])    
    nomes_filme.append(i[1])]
    
ratings_printed
nomes_filme

grafico_linha = px.line(x = nomes_filme, y = ratings_printed, width=1000, 
height=1000, title='Os Maiores do Cinema - Avaliação IMDB',
color_discrete_sequence=px.colors.qualitative.Alphabet,
template = 'plotly_dark')

grafico_linha.show()

!pip install dash
import dash
from dash import Dash, dcc, html, Input, Output

app = Dash(__name__)

app.layout = html.Main([
    html.Div(className="vertical-container", children=[
        html.H1("DASH: Os Maiores do Cinema - Avaliações"),
    ]),
    html.Div(children=[
        html.Div(className='horizontal-container', children=[
            html.Label('Selecione o intervalo de quantidade:'),
            dcc.RangeSlider(min=0, max=100, step=10, value=[0, 100],
                            id='slider-nota', className='slider'),
        ]),
        dcc.Graph(
            id='avaliaçõesMS'
        )
    ])
])

@app.callback(
    Output('avaliaçõesMS', 'figure'),
    Input('slider-nota', 'value')
)
def update_graph(range_value):
  ratings_IMDB = []
  ratings_MS = []
  for i in lista:
    if i[6] not in ratings_IMDB:
      ratings_IMDB.append(i[6])    
      ratings_MS.append(i[8])
  grafico_linha2 = px.line(x = ratings_IMDB, y = ratings_MS, width=1000, height=1000, title='Avaliação IMDB vs Avaliação Meta Score', color_discrete_sequence=px.colors.qualitative.Vivid, template = 'plotly_dark')
  grafico_linha2

if __name__ == '__main__':
    app.run_server(debug=True)
    
    
@import url('https://fonts.googleapis.com/css2?family=Roboto+Condensed:wght@400;700&display=swap');

* {
    margin: 0;
    padding: 0;
}

html,
body {
    background-color: #111111;

    color: #f6f6f6;
    font-family: 'Open Sans', sans-serif;
}

main {
    margin: 0 auto;
    width: 100vw;
}

h1 {
    margin: 1.5rem 0;
}

.vertical-container {
    width: 1000%;

    display: flex;
    flex-direction: line;
    align-items: center;
    justify-content: center;
}

.horizontal-container {
    width: 1000%;

    display: flex;
    flex-direction: line;
    align-items: center;
    justify-content: space-around;
}

.slider {
    width: 100%;
}

.dash-graph {
    width: inherit;
}
