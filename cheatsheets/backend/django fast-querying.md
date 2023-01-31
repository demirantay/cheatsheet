## Fast Querying in Django

Without writing custom SQL queries


Before writing the all
```python
def orm_queries_test_view(request):
    users = User.objects.order_by("id")[:100]
    data = {}
    for user in users:
        data[user.id] = {
            "groups_total": user.groups.count(),
            "is_staff":  user.groups.filter(name__in=['admin', 'superuser']).exists(),
        }
    return render(request, "sample/orm_queries_test.html", {"data": data})
```

Faster with prefetch
```python
def orm_queries_test_view(request):
    users = User.objects.prefetch_related("groups").order_by("id")[:100]
    data = {}
    for user in users:
        data[user.id] = {
            "groups_total": user.groups.count(),
            "is_staff":  user.groups.filter(name__in=['admin', 'superuser']).exists(),
        }
    return render(request, "sample/orm_queries_test.html", {"data": data})
```

Even better:
```python
def orm_queries_test_view(request):
    staff_groups = Group.objects.filter(name__in=["admin", "superuser"])
    users = User.objects.prefetch_related(
        “groups”,
        Prefetch("groups", to_attr="staff_groups", queryset=staff_groups),
    ).order_by("id")[:100]

    data = {}
    for user in users:
        data[user.id] = {
            "groups_total": user.groups.count(),
            "is_staff": len(user.staff_groups) > 0,
        }
    return render(request, "sample/orm_queries_test.html", {"data": data})
```
