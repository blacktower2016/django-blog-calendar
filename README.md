# django-blog-calendar
### HTML calendar for blog.


**BlogCalendar** provides html calendar for **Django** model containing
the date field. If model items do exist for the particular date,
BlogCalendar adds html link to the date-based url.


Example:
```python
    
    from simpleblog.models import Post
    from simpleblog.helpers.blog_calendar import BlogCalendar
    
    # args
    model = Post                      # django model with DateField or DateTimeField
    date_field = 'created'            # DateField or DateTimeField name in the model
    url_name = 'simpleblog:calendar'  # url name for links
                                      # url should have <year> <month> and <day> parameters

    # kwargs:
    additional_filters = {'is_public':True}  # additional filtering instructions
                                             # default is None

    day_abbr = ['Mo','Tu','We','Th','Fr','Sa','Su'] # days of week abbreviations
                                                    # default is calendar.day_abbr from python calendar module

    blog_calendar = BlogCalendar(
                    model,
                    date_field,
                    url_name,
                    additional_filters=additional_filters,
                    day_abbreviations=day_abbr
                )

    # html calendar for current month
    current_date = date.today()
    print (blog_calendar.formatmonth(current_date.year, current_date.month))

    # html calendar for current year
    print (blog_calendar.formatyear(current_date.year))
```
Tested with Django 1.11
