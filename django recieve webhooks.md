Links: [[PROGRAMMING]] - [[PYTHON]]
Rel: [[django]]

--- 
A webhook reciever is just an endpoint that accepts POST requests:
```py
import json
from django.http import HttpResponse
from django.views.decorators.csrf import csrf_exempt
from django.views.decorators.http import require_POST

@csrf_exempt
@require_POST
def webhook_endpoint(request):
    jsondata = request.body
    data = json.loads(jsondata)
    for answer in data['form_response']['answers']: # go through all the answers
      type = answer['type']
      print(f'answer: {answer[type]}') # print value of answers

return HttpResponse(status=200)
```

or simply,
create a url:
```py
path('/accept-hook', views.accept_webhook)
```
and collect POST data in the view:
```py
def accept_webhook(request):
	return request.POST.get('desired_key')
```

--- 
-> https://medium.com/@raiderrobert/how-to-make-a-webhook-receiver-in-django-1ce260f4efff (full example)

References:
- https://stackoverflow.com/questions/53974149/django-create-webhook-receiver
- https://www.reddit.com/r/django/comments/5ftsy6/how_do_i_create_a_callback_url_to_consume_a/
