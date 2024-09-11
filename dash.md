Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: [home](https://dash.plotly.com/)

dash (dashboards w/ [[plotly]]) 

--- 

Stopped at #4 "Live Graphs w/ Events": (Sentdex) [yt](https://www.youtube.com/watch?v=37Zj955LFT0&list=PLQVvvaa0QuDfsGImWNt1eUEveHOepkjqt&index=4  )

basic_dash_callback.py
```
import dash
import dash_core_components as dcc
import dash_html_components as html
from dash.dependencies import Input, Output

# https://dash.plot.ly/getting-started-part-2

external_stylesheets = ['https://codepen.io/chriddyp/pen/bWLwgP.css']

app = dash.Dash(__name__, external_stylesheets=external_stylesheets)

app.layout = html.Div([
    dcc.Input(id='my-id', value='initial value', type='text'),
    html.Div(id='my-div')
])


@app.callback(
    Output(component_id='my-div', component_property='children'),
    [Input(component_id='my-id', component_property='value')]
)
def update_output_div(input_value):
    return 'You\'ve entered "{}"'.format(input_value)


if __name__ == '__main__':
    app.run_server(debug=True)
```

dashtut.py
```
import dash
from dash.dependencies import Input, Output
import dash_core_components as dcc
import dash_html_components as html

import pandas_datareader.data as web
import datetime

start = datetime.datetime(2018, 1, 1)
end = datetime.datetime.now()

stock = 'TSLA'
df = web.DataReader(stock, 'yahoo', start, end)

app = dash.Dash()

app.layout = html.Div(children=[
	html.Div(children='''
		symbol to graph:
		'''),
	dcc.Input(id='input', value='', type='text'),
	html.Div(id='output-graph')
])

@app.callback(
	Output(component_id='output-graph', component_property='children'),
	[Input(component_id='input', component_property='value')]
	)

def update_graph(input_data):
	start = datetime.datetime(2018, 1, 1)
	end = datetime.datetime.now()
	df = web.DataReader(input_data, 'yahoo', start, end)

	return dcc.Graph(
		id='example-graph',
		figure={
			'data': [
			{'x': df.index, 'y': df.Close, 'type': 'line', 'name': input_data},
			# {'x': [1,2,3], 'y': [2,4,5], 'type': 'bar', 'name': u'Montreal'}
				],
			'layout': {'title': input_data
			}
		}
	)



""" TWO:
start = datetime.datetime(2018, 1, 1)
end = datetime.datetime.now()

stock = 'TSLA'
df = web.DataReader(stock, 'yahoo', start, end)

app.layout = html.Div(children=[
	html.H1(children='Hello Dash'),
	html.Div(children='''
		Dash: A web application framework for Python
		'''),

	dcc.Graph(
		id='example-graph',
		figure={
			'data': [
			{'x': df.index, 'y': df.Close, 'type': 'line', 'name': stock},
			# {'x': [1,2,3], 'y': [2,4,5], 'type': 'bar', 'name': u'Montreal'}
				],
			'layout': {'title': stock
			}
		}
	)
])
"""

""" ONE:
# app.layout = html.Div([
# 	dcc.Input(id='input', value='Enter something here!', type='text'),
# 	html.Div(id='output')
# 	])

# @app.callback(
# 	Output(component_id='output', component_property='children'),
# 	[Input(component_id='input', component_property='value')]
# 	)

# def update_value(input_data):
# 	return 'Input: {}'.format(input_data)
"""

if __name__ == '__main__':
	app.run_server(debug=True)
```

pandtest.py
```
import pandas_datareader.data as web
import datetime

start = datetime.datetime(2018, 1, 1)
end = datetime.datetime(2019, 1, 1)

df = web.DataReader('TSLA', 'yahoo', start, end)
print(df.head())
```


requirements.txt
```
Flask=1.0.2
Jinja2=2.10
MarkupSafe=1.1.1
Werkzeug=0.14.1
attrs=18.2.0
click=7.0
dash=0.38.0
dash-core-components=0.43.1
dash-html-components=0.13.5
dash-renderer=0.19.0
dash-table=3.5.0
decorator=4.3.2
flask-compress=1.4.0
ipython-genutils=0.2.0
itsdangerous=1.1.0
jsonschema=3.0.0
jupyter-core=4.4.0
nbformat=4.4.0
plotly=3.6.1
pyrsistent=0.14.11
retrying=1.3.3
traitlets=4.3.2
```