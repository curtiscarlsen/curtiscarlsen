## Tasks Started or Due Now
```tasks
			# Only tasks that are not done, that is, which begin like this (but without the quotes):
			#   '- [ ] ' or
			#   '* [ ] ' or
			#   '1. [ ] '
			# Indented tasks are supported, but only single-line tasks.
			not done

			# Tasks due today or earlier:
			 (due before tomorrow) OR ((starts before tomorrow) AND  (has start date))
			
			# Restrict to at most 100 tasks.
			# If you ask Tasks to display many hundreds or thousands of tasks,
			# Obsidian's editing performance really slows down.
			limit 100
			
			# Group and sort the output:
			group by filename
			sort by due reverse
			sort by description
			
			# Optionally, ask Tasks to explain how it interpreted this query:
			# explain
```


## Tasks Not started

```tasks
# Only tasks that are not done, that is, which begin like this (but without the quotes):
#   '- [ ] ' or
#   '* [ ] ' or
#   '1. [ ] '
# Indented tasks are supported, but only single-line tasks.
not done

# Tasks due after today:
(due after today) OR (no due date)

# Restrict to at most 100 tasks.
# If you ask Tasks to display many hundreds or thousands of tasks,
# Obsidian's editing performance really slows down.
limit 100

# Group and sort the output:
group by filename
sort by due reverse
sort by description

# Optionally, ask Tasks to explain how it interpreted this query:
# explain
```

## **------ All Pending Tasks  ------**
```tasks
# Only tasks that are not done, that is, which begin like this (but without the quotes):
#   '- [ ] ' or
#   '* [ ] ' or
#   '1. [ ] '
# Indented tasks are supported, but only single-line tasks.
not done

# pay no attention to dates:
# due before tomorrow

# Restrict to at most 100 tasks.
# If you ask Tasks to display many hundreds or thousands of tasks,
# Obsidian's editing performance really slows down.
limit 100

# Group and sort the output:
group by filename
sort by due reverse
sort by description

# Optionally, ask Tasks to explain how it interpreted this query:
# explain
```


#admin