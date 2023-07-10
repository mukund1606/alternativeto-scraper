
---
# AlternativeTo
## Hi, Welcome to AlternativeTo Web Scraper Documentation.

### Scrape latest apps from [AlternativeTo](https://alternativeto.net/)

### Provides search feature to search for apps

### Scrape app details and it's alternatives with many different filters

### Import `AlternativeTo` class from `scrape_up.alternativeto` module.

```python
from scrape_up.alternativeto import AlternativeTo
```

### Create an instance of `AlternativeTo` class.

```python
scraper = AlternativeTo("chrome")       # Provide With Available Browser
```
#### Currently Supports Chrome, Edge and Firefox only


| Methods              | Details                                                               |
| -------------------- | --------------------------------------------------------------------- |
| `.new_apps()`    | Returns a list of new apps from AlternativeTo.           |
| `.most_viewed()`      | Returns a list of most viewed apps from AlternativeTo.    |
| `.trending()`    | Returns a list of trending apps from AlternativeTo. |
| `.crew_picked()`     | Returns a list of crew picked apps from AlternativeTo.                                         |
| `.discontinued()`    | Returns a list of discontinued apps from AlternativeTo.                                             |
| `.get_alternatives(app_id, feature=None, platform=None, sort=None, app_license=None, hide_legal_warning=True, page=1)` | Returns a dictionary of the app and its alternatives.      |
| `.search_app(name, page=1)`   | Returns a list of apps matching the name.                             |

## **Examples**

### New Apps, Most Viewed Apps, Trending, Crew Picked, Discontinued
```python
from scrape_up.alternativeto import AlternativeTo

scraper = AlternativeTo("chrome")
new_apps = scraper.new_apps()
crew_picked = scraper.crew_picked()
most_viewed = scraper.most_viewed()
trending = scraper.trending()
discontinued = scraper.discontinued()

if new_apps is not None:
    for app in new_apps:
        print("Name:", app["name"])
        print("ID:", app["id"])
        print("Description:", app["description"])
else:
    print("Failed to retrieve new apps.")

if crew_picked is not None:
    for app in crew_picked:
        print("Name:", app["name"])
        print("ID:", app["id"])
        print("Description:", app["description"])
else:
    print("Failed to retrieve crew picked apps.")

if most_viewed is not None:
    for app in most_viewed:
        print("Name:", app["name"])
        print("ID:", app["id"])
else:
    print("Failed to retrieve most viewed apps.")

if trending is not None:
    for app in trending:
        print("Name:", app["name"])
        print("ID:", app["id"])
else:
    print("Failed to retrieve trending apps.")

if discontinued is not None:
    for app in discontinued:
        print("Name:", app["name"])
        print("ID:", app["id"])
else:
    print("Failed to retrieve discontinued apps.")
```
#### Output - 
```text
    New Apps or Crew Picked ->
        Name: {app_name}
        ID: {app_id}
        Description: {app_description}
        Name: {app_name}
        ID: {app_id}
        Description: {app_description}
    Trending, Most Viewed or Discontinued ->
        Name: {app_name}
        ID: {app_id}
        Name: {app_name}
        ID: {app_id}
```

## Get Alternatives
```python
scraper = AlternativeTo("chrome")
data = scraper.get_alternatives(
    "youtube",
    page=1,
    sort="rank",
    app_license="free",
)
if data is not None:
    print("Name:", data["name"])
    print("Alternative Apps")
    for alt_app in data["alternative_apps"]:
        print("Name:", alt_app["name"])
        print("ID:", alt_app["id"])
else:
    print("Failed to retrieve alternative apps.")
```
#### Output - 
```txt
    Name: {app_name}
    Alternative Apps
    Name: {alternative_app_name}
    ID: {alternative_app_id}
```

## Search Apps
```python
scraper = AlternativeTo("chrome")
data = scraper.search_app("photoshop",page=1)
if data is not None:
    print("Search Results")
    for app in data:
        print("Name:", app["name"])
        print("ID:", app["id"])
else:
    print("Failed to retrieve alternative apps.")
```
#### Output - 
```txt
    Search Results
    Name: {app_name}
    ID: {app_id}
```
---