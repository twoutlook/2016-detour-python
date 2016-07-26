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
This is a hard-coding, testing purpose.
```
def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    output = ', '.join([q.question_text for q in latest_question_list])
    return HttpResponse(output)
```
We actually get result like this,
```
    Where's question 4, I thought I saved that., question 5 xxx, 做為問卷調查的工具, 填入資料後,是否可以查看?, What's up?
```
### (2-1) add templae file polls/templates/polls/index.html
```
{% if latest_question_list %}
    <ul>
    {% for question in latest_question_list %}
        <li><a href="/polls/{{ question.id }}/">{{ question.question_text }}</a></li>
    {% endfor %}
    </ul>
{% else %}
    <p>No polls are available.</p>
{% endif %}
```
### (2-2) adjust index view in polls/views
```
...
from django.template import loader

def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    template = loader.get_template('polls/index.html')
    context = {
        'latest_question_list': latest_question_list,
    }
    return HttpResponse(template.render(context, request))
...
```

### (2-3) We get much desired result

```
    Where's question 4, I thought I saved that.
    question 5 xxx
    做為問卷調查的工具
    填入資料後,是否可以查看?
    What's up?
```
## Render is better than HttpResponse

```
...
from django.shortcuts import render

def index(request):
    latest_question_list = Question.objects.order_by('-pub_date')[:5]
    context = {'latest_question_list': latest_question_list}
    return render(request, 'polls/index.html', context)
...
```
- 這是完全取代之前代碼，有時候不太確定是不是真的有效，故意先將[:5]改成[:3]就知道了

## Show actual detial and also handle 404 

### (1)edit detail
```
...
def detail(request, question_id):
    try:
        question = Question.objects.get(pk=question_id)
    except Question.DoesNotExist:
        raise Http404("Question does not exist")
    return render(request, 'polls/detail.html', {'question': question})
...
```
### (2)create polls/templates/polls/detail.html
```
{{ question }}
```

## A better way to render detail and enhance detail content 

### (1)edit detail
```
...
from django.shortcuts import get_object_or_404, render

def detail(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    return render(request, 'polls/detail.html', {'question': question})
```
### (2)create polls/templates/polls/detail.html
```
<h1>{{ question.question_text }}</h1>
<ul>
{% for choice in question.choice_set.all %}
    <li>{{ choice.choice_text }}</li>
{% endfor %}
</ul>
```

## Easy or Hard lesson to remove hardcoded index
