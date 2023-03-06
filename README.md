## Introduction

The Django ORM is a powerful tool for building complex web applications. One of its key features is the ability to define relationships between database tables using foreign keys. However, when these relationships are deleted, it can create inconsistencies in the database. Django provides in-Python options for on_delete clauses to handle these cascading deletes, but this approach can be inefficient and prone to errors.

The proposed solution is to add support for database-level cascading options in the Django ORM. This will allow the database to handle the cascading of foreign key relationships with its native implementation. By leveraging the database's built-in functionality, the ORM can handle cascading deletes more efficiently and with greater reliability.

This project builds on existing work on the Django ticket to add support for database-level cascading options. The goal is to create a first-pass solution for a single database backend, generalize it to work with all supported database backends, integrate it with the migrations framework, write documentation, and perform extensive testing. The expected outcome is a significant improvement to the Django ORM that will improve the performance and reliability of applications that use it.

## Background
There is an old ticket on the Django project to add support for database-level cascading options, which was filed back in 2014 (https://code.djangoproject.com/ticket/21961). The ticket proposes the addition of a new option called db_on_delete, which would allow the database to handle the cascading of foreign key relationships using its native implementation, instead of relying on Django's in-Python options for on_delete clauses. The proposal suggests that the existing on_delete option could be used with the value DO_NOTHING if required.

Since the proposal was filed, there have been a couple of pull requests that were in the right direction (1: https://github.com/django/django/pull/14550, 2: https://github.com/django/django/pull/8661). These pull requests attempted to add support for database-level cascading options to the Django ORM. However, they were not merged due to various reasons.

The ticket has also sparked a long discussion on the Django-developers mailing list (https://groups.google.com/g/django-developers/c/FJMoGgtYIX4/m/LTdjlWydJ2EJ), where developers have debated the pros and cons of implementing this feature. Some of the concerns raised include differences in behavior across different database backends and potential performance implications of using database-level cascading options.

Despite these challenges, adding support for database-level cascading options to the Django ORM would be a valuable addition that could improve the performance and reliability of applications that use the ORM. Therefore, the objective of this project is to make the first-pass work generally for all database backends and integrate it with the migrations framework.
