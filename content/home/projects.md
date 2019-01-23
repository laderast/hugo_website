+++
# Projects widget.
widget = "projects"
active = true
date = "2016-04-20T00:00:00"

title = "Shiny Apps"
subtitle = "I love using the [shiny](http://shiny.rstudio.com) app framework for both data exploration in research and teaching. Click any of these links to go to the app."

# Order that this section will appear in.
weight = 19

# Content.
# Display content from the following folder.
# For example, `folder = "project"` displays content from `content/project/`.
folder = "project"

# View.
# Customize how projects are displayed.
# Legend: 0 = list, 1 = cards.
view = 1

# Filter toolbar.

# Default filter index (e.g. 0 corresponds to the first `[[filter]]` instance below).
filter_default = 0

# Add or remove as many filters (`[[filter]]` instances) as you like.
# Use "*" tag to show all projects or an existing tag prefixed with "." to filter by specific tag.
# To remove toolbar, delete/comment all instances of `[[filter]]` below.
[[filter]]
  name = "All"
  tag = "*"

[[filter]]
  name = "Research"
  tag = ".research"

[[filter]]
  name = "Teaching"
  tag = ".teaching"

+++

