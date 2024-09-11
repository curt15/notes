Links: [[PROGRAMMING]] - [[PYTHON]]

--- 
view
```py
from django.shortcuts import render
from django.views.generic import ListView #when to use?
from django.contrib.auth.decorators import login_required
from django.utils.decorators import method_decorator
from .models import *
from .forms import *

@method_decorator(login_required, name='dispatch')
class ProgramView(ListView):
	context_object_name = 'workout_list'
	template_name = 'program/extended.html'
	# queryset = Profile.objects.get(user=user)

	def get_queryset(self):
		# queryset = super(ProgramView, self).get_queryset()
		return Profile.objects.filter(user=self.request.user)

	def get_context_data(self):
		context = super(ProgramView, self).get_context_data()
		context['blocks'] = Block.objects.filter(user_id=self.request.user)
		context['workout_list'] = Workout.objects.filter(user_id=self.request.user)
		context['exercise_list'] = Exercise.objects.filter(user_id=self.request.user)
		context['set_list'] = Set.objects.filter(user_id=self.request.user)
		return context

# Create your views here.
# def program_detail_view(request):
# 	obj = Block.objects.get()
# 	my_context = {
# 		"my_text": "This is about us",
# 		"my_number": 123
# 	}
# 	return render(request, 'program/extended.html', my_context)

# 	def get_queryset(self):
# 		return models.objects.all()
```

user views
```py
from django.shortcuts import render, redirect, get_object_or_404
from django.contrib import messages
from django.contrib.auth.models import User
from django.contrib.auth.decorators import login_required
from django.views.generic import UpdateView #, CreateView, DeleteView

from .forms import UserRegisterForm, ProfileRegisterForm
from program.models import Profile


# Create your views here.

def register(request):
	if request.method == 'POST':
		form = UserRegisterForm(request.POST)
		if form.is_valid():
			form.save()
			username = form.cleaned_data.get('username')
			messages.success(request, 'Account created for {}! You are now able to login'.format(username))
			return redirect('/login')
	else:
		form = UserRegisterForm() # empty
	return render(request, 'users/register.html', {'form': form})

# different in class based views...
@login_required
def profile_view(request):
	if request.method == 'POST':
		form = ProfileRegisterForm(request.POST) #instance=request.user.profile for updateview
		if form.is_valid():
			profile = form.save(commit=False)
			profile.user = request.user
			profile.bwt = form.cleaned_data.get('bwt')
			profile.height = form.cleaned_data.get('height')
			profile.birthday = form.cleaned_data.get('birthday')
			profile.gender = form.cleaned_data.get('gender')
			profile.save()
			form.save()
			# bwt = form.cleaned_data.get('bwt')
			# height = form.cleaned_data.get('height')
			# birthday = form.cleaned_data.get('birthday')
			# gender = form.cleaned_data.get('gender')
			messages.success(request, 'Profile update success!')
			return redirect('/profile/')
	else:
		form = ProfileRegisterForm()
	return render(request, 'users/profile.html', {'form': form})

@login_required
def profile_update_view(request, id):
	instance = get_object_or_404(Profile, id=id)
	if request.method == 'POST':
		form = ProfileRegisterForm(request.POST or None, instance=instance)
		if form.is_valid():
			profile = form.save(commit=False)
			profile.user = request.user
			profile.bwt = form.cleaned_data.get('bwt')
			profile.height = form.cleaned_data.get('height')
			profile.birthday = form.cleaned_data.get('birthday')
			profile.gender = form.cleaned_data.get('gender')
			profile.save()
			form.save()
			messages.success(request, 'Profile update success!')
			return redirect('edit')
	else:
		form = ProfileRegisterForm(instance=request.user.profile)
	return render(request, 'users/profile.html', {'form':form})

# class ProfileUpdate(generic.DetailView):
# def profile_update(request, id=None):
# 	object = Profile.objects.get(id=id)
# 	form = ProfileRegisterForm(instance=object)
# 	return render(request, 'users/register.html', {'form':form})

```