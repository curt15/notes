Links: [[PYTHON]] - [[PROGRAMMING]]
Rel: [[python 3rd party packages]]
Ref: https://plotly.com/python/
Tags: #public 

--- 
**plotly3dmesh.py**

```py
import plotly.graph_objs as go

def examp3dmesh():
	"""
	eight_cube_verts = {
		x=[0, 0, 1, 1, 0, 0, 1, 1],
		y=[0, 1, 1, 0, 0, 1, 1, 0],
		z=[0, 0, 0, 0, 1, 1, 1, 1],
		}
	"""
	fig = go.Figure(data=[
                go.Mesh3d(
			        x=[n for n in range(1,1001)],
			        y=[n for n in range(1,1001)],
			        z=[n for n in range(1,1001)],
                          )])
	return fig.show()



if __name__ == '__main__':
	examp3dmesh()
```