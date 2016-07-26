#  take note of <b>Writing your first Django app, part 3</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/tutorial03/

## Write views to ensure parsing and routing
### (1) add def to polls/views.py
```
def detail(request, question_id):
    return HttpResponse("You're looking at question %s." % question_id)

def results(request, question_id):
    response = "You're looking at the results of question %s."
    return HttpResponse(response % question_id)

def vote(request, question_id):
    return HttpResponse("You're voting on question %s." % question_id)
```
### (2) add urlpatterns to polls/urls.py
```

urlpatterns = [
    # ex: /polls/
    url(r'^$', views.index, name='index'),
    # ex: /polls/5/
    url(r'^(?P<question_id>[0-9]+)/$', views.detail, name='detail'),
    # ex: /polls/5/results/
    url(r'^(?P<question_id>[0-9]+)/results/$', views.results, name='results'),
    # ex: /polls/5/vote/
    url(r'^(?P<question_id>[0-9]+)/vote/$', views.vote, name='vote'),
]
```
### (3) check http://localhost:8000/polls/12345/
    You're looking at question 12345.


## Write actual views 
### (1) edit index on polls/views.py
```
def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    output = ', '.join([q.question_text for q in latest_question_list])
    return HttpResponse(output)
```
We actually get result like this,
    Where's question 4, I thought I saved that., question 5 xxx, 做為問卷調查的工具, 填入資料後,是否可以查看?, What's up?