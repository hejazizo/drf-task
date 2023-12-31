# Django Rest Framework Task
Task: LinkedIn User Profile Backend API

Your task is to create a backend API using Django Rest Framework for a LinkedIn User profile. The API should allow users to authenticate, view and edit their profile information, add education items, and perform CRUD operations on their education items.

Requirements:

1. User Profile:
   - The User profile should have the following fields:
     - `username` (_string_): The username of the user.
     - `email` (_string_): The email address of the user.
     - `location` (_string_): The location of the user.
     - `gender` (_string_): The gender of the user.
     - `avatar` (_file_): The avatar image of the user.
     - `is_verified` (_boolean_): Indicates whether the user's profile is verified.

2. Authentication:
   - Users should be able to authenticate using their credentials (username/email and password) to access the API.

3. Profile Operations:
   - Users should be able to view their own profile information.
   - Users should be able to edit their profile information, including username, email, location, gender, and avatar.
   - The avatar should be uploaded as a file and stored on the server.

4. Education Items:
   - Users should be able to add education items to their profile.
   - Each education item should have the following fields:
     - `institution` (_string_): The name of the institution.
     - `degree` (_string_): The degree obtained.
     - `field_of_study` (_string_): The field of study.
     - `start_date` (_date_): The start date of the education.
     - `end_date` (_date_): The end date of the education.
     - `description` (_string_): A description of the education item.

5. CRUD Operations on Education Items:
   - Users should be able to perform CRUD operations (Create, Read, Update, Delete) on their education items.
   - Users should be able to view all their education items.
   - Users should be able to edit an existing education item.
   - Users should be able to delete an existing education item.

Optional Bonus Tasks:

1. Test Cases:
   - Write test cases to verify the functionality of the API endpoints.
   - Include both unit tests and integration tests.
   - Ensure proper coverage of different scenarios and edge cases.

2. Performance Measurement with Locust:
   - Use Locust to measure the performance of the API endpoints under different load conditions.
   - Define appropriate test scenarios and performance metrics.
   - Analyze the results and identify any bottlenecks or areas for optimization.

3. Other Improvements:
   - Implement additional features or enhancements to improve the overall functionality, security, or performance of the API.
   - Suggestions for improvements may include pagination, filtering, sorting, input validation, error handling, or API documentation enhancements.


Guidelines:

- Use Django Rest Framework to build the API.
- Use appropriate authentication mechanisms (e.g., token-based authentication) to secure the API endpoints.
- Use Django models and serializers to define the User profile and Education item structures.
- Write clear and concise code with proper error handling and validation.
- Include proper documentation for the API endpoints and how to use them.

To complete the task, you can start by creating the Django project and app. Define the necessary models and serializers for the User profile and Education items. Implement the authentication views and API endpoints for profile operations and CRUD operations on education items.

Feel free to use the provided Python code as a starting point.

```python
# models.py
from django.db import models
from django.contrib.auth.models import AbstractUser


class User(AbstractUser):
    name = models.CharField(max_length=255)
    location = models.CharField(max_length=255)
    gender = models.CharField(max_length=20)
    avatar = models.ImageField(upload_to='avatars/')
    is_verified = models.BooleanField(default=False)


class Education(models.Model):
    user = models.ForeignKey(User, on_delete=models.CASCADE, related_name='education')
    institution = models.CharField(max_length=255)
    degree = models.CharField(max_length=100)
    field_of_study = models.CharField(max_length=100)
    start_date = models.DateField()
    end_date = models.DateField()
    description = models.TextField()


# serializers.py
from rest_framework import serializers
from .models import User, Education


class UserSerializer(serializers.ModelSerializer):
    pass

class EducationSerializer(serializers.ModelSerializer):
    pass


# views.py
from rest_framework import viewsets

class UserProfileViewSet(viewsets.ModelViewSet):
    pass

class EducationViewSet(viewsets.ModelViewSet):
    pass

```


Good luck with your task!

